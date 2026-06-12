---
title: "Ubuntu behind Proxy server"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by stuart.crouch on 2010-11-19
Hope this is the right forum.  I set up a VirtualBox at work so I could do things that I find easy in linux on linux whilst still running a Windows machine.

I got the VM with ubuntu 10.10 on it and started installing the things I need when I hit a snag, we are behind a proxy server here.  I found the configuration System -> Preferences -> Network proxy and entered the proxy information.  I clicked apply system wide and then tried accessing the internet.

Success! Firefox allows me to browse around, and sudo apt-get update also worked.

Next I tried to download flash.  I tried visiting youtube.com and following ubuntus automated installer.  That failed stating that it couldnt reach the server, so I visited [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) to try and do it manually.

Now when I try to upgrade I get this 

```

sac76@pccs1438-VirtualBox:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse flashplugin-installer i386 10.1.102.65ubuntu0.10.10.1 [20.2kB]
Fetched 20.2kB in 0s (225kB/s)           
Preconfiguring packages ...
(Reading database ... 125996 files and directories currently installed.)
Preparing to replace flashplugin-installer 10.1.102.64ubuntu0.10.10.1 (using .../flashplugin-installer_10.1.102.65ubuntu0.10.10.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Setting up flashplugin-installer (10.1.102.65ubuntu0.10.10.1) ...
Downloading...
--2010-11-19 10:50:05--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-11-19 10:50:27--  (try: 2)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

--2010-11-19 10:50:50--  (try: 3)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65.orig.tar.gz
Connecting to archive.canonical.com|91.189.88.33|:80... 


```

When I click the link it loads firefox and downloads the file just fine.  Does anyone know why apt-get cant reach archive.canonical.com?  I'd also like to install kerebos and some other stuff so I can connect to my works NT domain, but they also fail because of time outs.

Thanks
--
Stuart

---

### Post by dino99 on 2010-11-19
****  archive.canonical.com|91.189.88.33|:80   ****

should not this be:

archive.canonical.com 91.189.88.33:80

???? is canonical blacklisted by your boss

---

### Post by stuart.crouch on 2010-11-19
> **dino99 said:**
> ****  archive.canonical.com|91.189.88.33|:80   ****

should not this be:

archive.canonical.com 91.189.88.33:80


I cant see the difference?  What I've pasted is what sudo apt-get upgrade spits out.

> ???? is canonical blacklisted by your boss

If it were then wouldn't ```
wget http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65.orig.tar.gz
``` also fail?  Because I can reach the file using wget. Its just apt-get that can't.

Thanks
--
Stuart

---

### Post by stuart.crouch on 2010-11-22
Bump? Anyone got any other suggestions or things to try?

---

### Post by rasti121 on 2011-08-10
I have the same issue (10 months later). I think the problem is that the flash update script ignores ANY proxy settings. I have tried:
1. system wide proxy as described above
2. browser proxies (firefox chrome etc... including through plugins on firefox)
3. Command line proxy environment variable HTTP_PROXY and http_proxy

I can get apt-get to work from command line, but since the flash update is connecting (infinitely probably, stopped it after 30-something retries) while ignoring proxy variables it doesn't work on a firewalled off network with HTTP proxy.

My virtual machine is on a laptop, so connecting directly to a WLAN "on the Internet" works and the script runs fine.

If I find out who is the developer of the script I'll ask them to support proxy variables, until then I think "direct" Internet connection is the only option.

---

