---
title: "FireFox"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by solo on 2005-08-03
Hi all.

I just think I made the FireFox-innstall right, but how do I start the program? What file should I open? I already have the old verision of FireFox, but it is in English, and the new one (that I am trying to start) is in Norwegian..

---

### Post by skatedawe on 2005-08-03
type

 "firefox" in term. ?

---

### Post by hypnos on 2005-08-04
How did you install Firefox? Using DEB package or Apt-get/Synaptic? System version of Firefox (1.0.2) is located in /usr/lib/mozilla-firefox. Your version can be in /usr/local/mozilla-firefox but that's not for sure.

---

### Post by erik-the-red on 2005-08-04
[QUOTE=hypnos]How did you install Firefox? Using DEB package or Apt-get/Synaptic? System version of Firefox (1.0.2) is located in /usr/lib/mozilla-firefox. Your version can be in /usr/local/mozilla-firefox but that's not for sure.[/QUOTE]
 Should I uninstall firefox through synaptic and then install 1.0.6 from source?

---

### Post by hypnos on 2005-08-05
[QUOTE=erik-the-red]Should I uninstall firefox through synaptic and then install 1.0.6 from source?[/QUOTE]

It's not nessesary. I had problems with upgrade FF too. I downloaded polish package with installer but after that came problem with using my profile.
Most improtant thing is to overwrite older version with the new one. And Synaptic does it.

I think that you have already 1.0.6 version but the language-pack extention is incompatible no more. In was so in my case.

---

### Post by erik-the-red on 2005-08-05
[QUOTE=hypnos]It's not nessesary. I had problems with upgrade FF too. I downloaded polish package with installer but after that came problem with using my profile.
Most improtant thing is to overwrite older version with the new one. And Synaptic does it.

I think that you have already 1.0.6 version but the language-pack extention is incompatible no more. In was so in my case.[/QUOTE]
 No, I am still using 1.0.2 - the default Hoary selection.

---

### Post by angkor on 2005-08-05
What happens if you do:

sudo apt-get update
sudo apt-get install mozilla-firefox

Cause Firefox 1.06 has already been released into the repos

```
apt-cache policy mozilla-firefox
mozilla-firefox:
  Installed: 1.0.6-0ubuntu0.1
  Candidate: 1.0.6-0ubuntu0.1
  Version table:
 *** 1.0.6-0ubuntu0.1 0
        500 http://security.ubuntu.com hoary-security/main Packages
        100 /var/lib/dpkg/status
     1.0.2-0ubuntu5 0
        500 http://nl.archive.ubuntu.com hoary/main Packages
```

Don't forget to delete the version you downloaded from Mozilla first.

---

### Post by Maxplayer14 on 2005-08-05
I am also having an issue.  I tried to updgrade through synaptic and now I can't even open Firefox.  When I try to install or uninstall Firefox I get several errors now.  I have manually deleted all my mozilla folders.  Now when I try to install Firefox from Synaptic I get these errors.

```
E: /var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb: 
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', 
which is also in package mozilla-firefox
```

Any idea?

---

### Post by angkor on 2005-08-05
@Maxplayer:

read this thread...I believe the answer to your problem is in there somewhere? Did you have the backport firefox installed?

[http://www.ubuntuforums.org/showthread.php?t=51943&highlight=firefox+1.06+update+backport](http://www.ubuntuforums.org/showthread.php?t=51943&highlight=firefox+1.06+update+backport)

---

### Post by Maxplayer14 on 2005-08-05
[QUOTE=angkor]@Maxplayer:

read this thread...I believe the answer to your problem is in there somewhere? Did you have the backport firefox installed?

[http://www.ubuntuforums.org/showthread.php?t=51943&highlight=firefox+1.06+update+backport](http://www.ubuntuforums.org/showthread.php?t=51943&highlight=firefox+1.06+update+backport)[/QUOTE]
 Well that worked in an odd way.  I could have sworn I had tried that already but anyway thanks, its working fine now.

---

### Post by erik-the-red on 2005-08-05
The apt-get upgrade and then install does not work for me. Apparently, I do not have the repositories you used in my list.

Which ones are they?

Is it really that hard to compile Firefox from source?

---

### Post by erik-the-red on 2005-08-05
[QUOTE=erik-the-red]The apt-get upgrade and then install does not work for me. Apparently, I do not have the repositories you used in my list.

Which ones are they?

Is it really that hard to compile Firefox from source?[/QUOTE]
 Never mind. I took a risk and uninstalled firefox via synaptic.

I then unzipped the .tar.gz from mozilla.org and it was actually a binary installer, not a ./configure, make, make install.

Nobody else did this?

---

### Post by hypnos on 2005-08-06
[QUOTE=erik-the-red]
I then unzipped the .tar.gz from mozilla.org and it was actually a binary installer, not a ./configure, make, make install.

Nobody else did this?[/QUOTE]

I did. And after that I had problems with profile which I've used. So I added backports to Synaptic and installed FF. Now I'm having no problems with browser. Everything's running and all my extentions works fine.

---

### Post by granite230 on 2005-08-15
Hi, I'm trying to install FTD4Linux.

One of my friends says I need 'mozilla-firefox-dev' but when I do: 'sudo apt-get install mozilla-firefox-dev' I get this error message:

Unpacking firefox-dev (from .../firefox-dev_1.0.6-1ubuntu1~5.04ubp1_i386.deb) ...
Errors were encountered while processing:
/var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
granite@granite://$

We both don't know what this is... I reinstalled Hoary today and reinstalled a lot of stuff. Last time I got this error message my browser wouldn't start anymore so I could reinstall everything again. Thank god my browser is still working this time...

I really don't get this... FTD4Linux has been working before, but when I try to install it myself, nothing seems to work...

here's the site: [http://www.ftd4linux.nl/](http://www.ftd4linux.nl/) it's Dutch.

---

