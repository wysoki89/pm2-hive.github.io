---
layout: docs
title: Monitoring
description: Monitoring applications
permalink: /docs/usage/monitoring/
---

## Monitoring CPU/Memory

<center>
<img src="/images/pm2-monit.png" title="PM2 Monit"/>
</center>

PM2 gives you a simple way to monitor the resource usage of your application.
You can monitor memory and CPU easily and straight from your terminal:

```bash
pm2 monit
```

## Dashboard monitoring

[![Keymetrics Dashboard](https://pm2.io/_nuxt/img/Personalized_metrics.ba73c4b.png)](https://app.pm2.io/#/register)

If you manage your Node.js application with PM2, we invite you to try Keymetrics. It makes monitoring and managing applications accross servers easier than ever.
Feel free to try it:

[Discover the monitoring dashboard for PM2](https://app.pm2.io/#/register)

## Memory threshold

PM2 allows to reload (auto fallback to restart) an application based on a memory limit. 
Please note that the PM2 internal worker (which checks memory and related), starts every 30 seconds, so you may have to wait a bit before your process gets restarted automatically after reaching the memory threshold.

### CLI

```bash
pm2 start big-array.js --max-memory-restart 20M
```

### JSON

```json
{
  "name"   : "max_mem",
  "script" : "big-array.js",
  "max_memory_restart" : "20M"
}
```

### Programmatic

```javascript
pm2.start({
  name               : "max_mem",
  script             : "big-array.js",
  max_memory_restart : "20M"
}, function(err, proc) {
  // Processing
});
```

### Units

Units can be K(ilobyte), M(egabyte), G(igabyte).

```
50M
50K
1G
```
