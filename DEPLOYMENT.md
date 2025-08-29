# SeatZ Frontend - Production Deployment Guide

## Quick Vercel Deployment

### Prerequisites
- Node.js 18+ installed
- Vercel CLI installed (`npm i -g vercel`)

### 1. Environment Setup
The frontend is already configured to use the Azure VM backend:
- **API URL**: `http://172.188.82.23:8000`
- **Environment**: Production

### 2. Deploy to Vercel

#### Option A: Using Vercel CLI
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

#### Option B: Using GitHub Integration
1. Go to [Vercel Dashboard](https://vercel.com)
2. Import the repository: `https://github.com/wasiffaisal10/SeatZ_Web`
3. Vercel will auto-detect the React app and deploy

#### Option C: Manual Build & Deploy
```bash
# Install dependencies
npm install

# Build for production
npm run build

# Deploy build folder to Vercel
vercel --prod
```

### 3. Environment Variables in Vercel
The following environment variables are already configured:
- `REACT_APP_API_URL=http://172.188.82.23:8000`
- `REACT_APP_ENV=production`

### 4. Performance Optimizations Applied

#### ✅ Code Splitting
- React app uses automatic code splitting
- Lazy loading for routes (if implemented)

#### ✅ Asset Optimization
- Minified CSS and JavaScript
- Optimized images and fonts
- Gzip compression enabled

#### ✅ Caching Strategy
- Static assets cached for 1 year
- API responses cached appropriately
- CDN distribution via Vercel Edge Network

#### ✅ Security Headers
- Content Security Policy (CSP)
- HTTPS enforcement
- XSS protection

### 5. Testing the Deployment

#### Local Testing
```bash
npm start
# Visit http://localhost:3000
```

#### Production Testing
After deployment, test:
- API connectivity to `http://172.188.82.23:8000`
- Course search functionality
- Alert creation and management
- Real-time updates

### 6. Monitoring & Analytics

#### Performance Monitoring
- Vercel Analytics (if enabled)
- Core Web Vitals tracking
- Error monitoring

#### API Monitoring
- Backend health checks
- Response time monitoring
- Error rate tracking

### 7. Troubleshooting

#### Common Issues
1. **CORS Errors**: Ensure backend CORS is configured for Vercel domains
2. **API Timeout**: Check Azure VM firewall and network settings
3. **Build Failures**: Verify all dependencies are listed in package.json

#### Debug Commands
```bash
# Check build locally
npm run build

# Test API connectivity
curl http://172.188.82.23:8000/api/realtime/courses

# Check Vercel logs
vercel logs
```

### 8. Scaling & Optimization

#### Frontend
- Enable Vercel Analytics
- Implement service worker for offline functionality
- Add Progressive Web App (PWA) features

#### Backend
- Consider adding a CDN for static assets
- Implement API rate limiting
- Add caching layer (Redis)

## Repository Structure
```
├── public/           # Static assets
├── src/
│   ├── components/   # React components
│   ├── pages/        # Route pages
│   ├── services/     # API services
│   └── utils/        # Helper functions
├── .env.production   # Production environment
├── vercel.json       # Vercel configuration
└── package.json      # Dependencies and scripts
```

## Support
For deployment issues, check:
- [Vercel Documentation](https://vercel.com/docs)
- [React Deployment Guide](https://create-react-app.dev/docs/deployment/)
- Backend API documentation at `http://172.188.82.23:8000/docs`