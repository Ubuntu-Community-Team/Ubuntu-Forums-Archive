---
title: "My latest attempt to upgrade chrome"
date: 2021-04-03
forum: Installation &amp; Upgrades
---

### Post by dbee on 2021-04-03
Got an red update notification on my chrome browser on xubuntu. Denoting that chrome needed an update over a week ago. 

> 
$ uname -a
Linux dara-HP-Stream-Laptop-11-y0XX 4.15.0-139-generic #143-Ubuntu SMP Tue Mar 16 01:30:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


Not a problem. Just follow the link to update right? Wrong. 

When I follow the link. It tells me that chrome needs to be reinstalled. From version 87 to 89 requires a complete reinstallation.

So I follow the link then the chrome .deb file. Bringing me to an install screen deadend. That gives me a repo notification and nothing else. I install 3 times. Nothing happens. No chrome update or installation.

Cue the command line. It seems I'm still on version 87. So I update all packages using apt. Still old version of chrome.

So then I upgrade xubuntu using apt. Google-chrome is one of the packages that gets upgraded. 

Back to the cli. google-chrome version 89 is now installed instead of the previous version 87.

Kill chrome. Then open again. Still the same red Update notification. Next step is a system restart. 

I'll see if that helps. I was under the impression though, that Linux didn't require a system restart for upgrading? Perhaps I'm wrong?

Seems like a lot of effort to go to in order to update chrome. What about a Linux newbie? What are they supposed to do exactly, in the same situation?

[https://i.ibb.co/NWxJpbB/chrome89-terminal.png](https://i.ibb.co/NWxJpbB/chrome89-terminal.png)

[https://i.ibb.co/Rz83grg/chrome-install.png](https://i.ibb.co/Rz83grg/chrome-install.png)

[https://i.ibb.co/JxqJ3k2/chrome-terminal.png](https://i.ibb.co/JxqJ3k2/chrome-terminal.png)

---

### Post by mikewhatever on 2021-04-03
Looks like there is a problem with Google's repository, or something it misconfigured at your end.
I'd check what repository is added, and what packages it contains. Restart is obviously not required, but if you insist, it's ok. 
Such problems shouldn't be unexpected, Xubuntu, if fact any distro, is probably not very high on Google Chrome maintainer's support list.

PS: Good thing I don't have to deal with any of that, and for"a Linux newbie" reading this thread, just use the default Firefox browser.

---

### Post by ActionParsnip on 2021-04-03
what is the output of:
```

ls /etc/apt/sources.list.d/* | grep -i chr

```
Thanks

---

### Post by CelticWarrior on 2021-04-03
> **ActionParsnip said:**
> what is the output of:
```

ls /etc/apt/sources.list.d/* | grep -i chr

```
Thanks

This ^^^ just to check out what other possible problems might be there.

ANY Google Chrome properly installed - I mean it in the utmost absolute terms - is updated along with all the other security, system and software updates, from the official Ubuntu repositories and third-parties (like Google's). So, unless the specific mirror for the Google Chrome repository in your part of the world (if it has different mirrors, I don't think that's the case) hasn't been working for a very long time, assuming that you have been installing the updates normally as you should then you should be running version [COLOR=#5F6368][FONT=Roboto]89.0.4389.90.[/FONT][/COLOR]

---

### Post by Impavidus on 2021-04-03
When you install Google Chrome from the .deb, it's supposed to put a software source for upgrades in /etc/apt/sources.list.d. Apt will then upgrade Google Chrome along with all other software it handles. It worked the last time I checked on Xubuntu, but after the last fresh install (July 2020) I haven't reinstalled Chrome.

One other thing that could be wrong is that the repositories are present, but there's a problem with the security key. Can you show the output of```
sudo apt-get update
apt-cache policy google-chrome-stable
```I hope I got the name of the package right.

---

### Post by coffeecat on 2021-04-03
@dbee, I've reduced your oversized images to URLs. Please be considerate of those using mobile devices and not use giant images. And there is no need to link to off-site image hosting sites. Simply use the paperclip icon in the advanced editor toolbar to upload any images you wish to include to the forum server. That way you get clickable thumbnails.

---

### Post by dbee on 2021-04-06
> 
dara@dara-HP-Stream-Laptop-11-y0XX:~$ ls /etc/apt/sources.list.d/* | grep -i chr/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome.list.save


> 
dara@dara-HP-Stream-Laptop-11-y0XX:~$ apt-cache policy google-chrome-stable
google-chrome-stable:
  Installed: 89.0.4389.114-1
  Candidate: 89.0.4389.114-1
  Version table:
 *** 89.0.4389.114-1 500
        500 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages
        100 /var/lib/dpkg/status


sorry coffeecat. will do. next time :-) Thanks.

---

