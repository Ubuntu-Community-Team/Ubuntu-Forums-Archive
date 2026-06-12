---
title: "dapper server pam_auth undefined"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Aramil Moonmist on 2008-01-19
recently at work we have switched servers to a rack mountable one. neither me nor the other programmer was involved in creating the original server, and the creator (fired earlier this year) left the thing a complete mess. weve managed to install ssh, apache, php, mysql, and get them all working the way they were before, except now every time someone tries to log in the site, we get the error warning message:

```
Fatal error: Call to undefined function pam_auth() in /var/www/login.php on line 61
```

the package php4-auth-pam is installed

were using php5 though and theres no php5-auth-pam file in dapper although i think there was one in gutsy. we have access to the old server so we can look at the old config files, but nothing immediately helps

thanks in advance

---

