---
title: "Install via local http"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by Jrgen_Staun on 2015-09-25
I have integrated our Ubuntu installations in our Windows Deployment Service ([https://www.nbalonso.com/deploy-linux-windows-server/](https://www.nbalonso.com/deploy-linux-windows-server/)) this works great if i use the official archive dk.archive.ubuntu.com. I managed to redirect this to my on Windows IIS http webserver and it works fine a long way down the road. But! - When it comes to files with + (multiply sign) in a file it fails with an error like - 
----------------------------
Debootstrap warning 
Warning: couldn't download packages locales (ver 2.13+git20120306-3arc all)
----------------------------

and this continues for all files with a + sign - at least thats what I think is the issue as the file is there - I can browse to the file via http, but when I click to download the file it fails with error that it does not exist.

If I install over FTP it works great.

Any ideas on how to come by this issue?

---

### Post by Jrgen_Staun on 2015-09-25
can you imagine - as I just send the message I realized the issue was IIS on my Windows 2012 server. It was the server that had issues with transcoding the + sign, so I had to add this section to my web.config file and it can now download the files correct.

> [COLOR=#111111][FONT=Verdana][I]<system.webServer>
[/I][/FONT][/COLOR]
[COLOR=#111111][FONT=Verdana]*    <security>*[/FONT][/COLOR]
[COLOR=#111111][FONT=Verdana]*            <requestFiltering allowDoubleEscaping="true" />*[/FONT][/COLOR]
[COLOR=#111111][FONT=Verdana]*    </security>*[/FONT][/COLOR]
[COLOR=#111111][FONT=Verdana][I]</system.webServer>

[COLOR=#222222][FONT=Verdana]

My next issue arised now - Configuring 'pkgsel' failed with error code 127??

Just love trouble shooting.[/FONT][/COLOR][/I][/FONT][/COLOR]

---

