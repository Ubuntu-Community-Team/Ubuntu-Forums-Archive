---
title: "** MOD-MONO woes...Can mod-mono-server4 work? **"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by mrrstrat on 2016-11-26
Like many other people I do software development and want to use Mono.

I have Ubuntu Server 16.04 setup with Apache2 and mod-mono-server4. I am trying to get the latest Xamarin MVC stuff to run and have well polluted my server with the bits and pieces of advice to get a functioning Mono server going.

How could it be that difficult???

Is there anyone with mod-mono-server4 running a real web site with Apache2 that can point me to an installation guide for Ubuntu Server (pardon the bluntness) THAT WORKS?

I have worked on it for days now (please don't laugh :-) ) - and am hardly a newbie to setting these things up. I must be missing something fundamental (such as server4 does not work or Xamarin Community does not work with server4).

Any expert advice?

Huge thanks in advance!

---

### Post by mrrstrat on 2016-11-26
I am setting up a PROD server and this is not a DEV server (looking to do 'the real deal' with this server. I am pulling my hair out as I cannot believe there is no latest How-to on Dev tools + Server Environment setup guides. Just lots of bits and pieces from 2005-present. And the questions that I see remaining unanswered (like mine) remain unanswered on forums.

#pleasehelp

Ok..so it works. Who would have figured following the MOD-MONO instructions and making sure every step is followed. I was a RTFM violator...

[h=2]ASP.NET MVC 5.2 - *live on Ubuntu Server 16.04*[/h]

Instructions at: [http://www.mono-project.com](http://www.mono-project.com)

And: most important steps: [COLOR=#000000][FONT=Menlo]sudo chmod -R 775 on the directory after FTP and *let the mod-mono tool on the mono-project.com site generate your Apache virtual site *[/FONT][/COLOR][FONT=Menlo][COLOR=#000000]*con file!!*[/COLOR][/FONT]

---

