---
title: "Problem With Software Updates"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by kwrxxx on 2007-04-07
When I try to get updates using the updates installer program in Ubuntu 6.10 I get the following errors. I have visited the referenced URL's and the update packages are there but the update program can not retrieve them. Here is the error:

```

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_2.0.3-0ubuntu3.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb
  404 Not Found





```

 If I have to how do I install the updates manually after downloading from the web site? I know with Fedrora I can use rpm -Uvh <packagename>



TIA

---

### Post by SoggyCornflake on 2007-04-07
> **kwrxxx said:**
> When I try to get updates using the updates installer program in Ubuntu 6.10 I get the following errors. I have visited the referenced URL's and the update packages are there but the update program can not retrieve them:


I've had the same problem and I think it's possibly a DNS issue.  I have KDE as my desktop and I found that when I could use Update Manager to update a package - getting the same result as you I could go to the web location using Konqueror.  If Konqueror could find the location, I could right away go back to Update Manager and it would find the package and do it's work like it was supposed to. 

I was also having problems with Fire Fox and when I posted my issues with FF, I was pointed to this [link]("http://ubuntuforums.org/showthread.php?t=87798").  I think they're related because both Firefox and Update manager couldn't seem to find a website, but once Konqueror found it, they'd both work normally.  At any rate, once I made the change explained in that link, I found that both FireFox and Update Manager haven't given many problems.  (If after a month neither give me problems, I'll truly believe that the issue is fixed.)

---

### Post by kwrxxx on 2007-04-07
Hi,
I logged out of Ubuntu and logged back in and it turned out I had 91 updates to apply. I then applied the updates and everything was downloaded and installed properly. If any one else has this problem logging out and back in may fix the problem. 

KWR

---

