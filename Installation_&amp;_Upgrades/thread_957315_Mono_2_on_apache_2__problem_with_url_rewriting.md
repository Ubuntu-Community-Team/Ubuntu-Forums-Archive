---
title: "Mono 2 on apache 2 : problem with url rewriting"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by KrisGarrein on 2008-10-24
Hey.

After quite some difficulty to get Mono 2.0 running on Apache 2 (mod_mono) on Ubuntu Server 8.04 LTS, I finally got it working.

I put BlogEngine.net on the server, which partially works.

When Url rewriting is used however, I get a 'resource cannot be found' error message :(

Can anyone guide me how to get the url rewriting working ?

I guess this problem might be caused by apache if apache checks if the files exist ?
In Windows/IIS there's simply an option 'check file exists', but I have no idea how to do it in apache.

Site with mono works: 
[http://blueprint.homedns.org:8083/www/default.aspx](http://blueprint.homedns.org:8083/www/default.aspx)

Url rewriting does not work:
[http://blueprint.homedns.org:8083/www/post/Welcome-to-BlogEngineNET-1-4.aspx](http://blueprint.homedns.org:8083/www/post/Welcome-to-BlogEngineNET-1-4.aspx)

Can anyone help me ?

Thank you !
K.

---

### Post by KrisGarrein on 2008-10-24
Hey.

Meanwhile somebody provided a solution on the website of the mono project.

Apparently the problem was in the BlogEngine code, not in apache or mono.

See [http://go-mono.com/forums/#nabble-to20096216%7Ca20149404](http://go-mono.com/forums/#nabble-to20096216%7Ca20149404)

Regards.

---

