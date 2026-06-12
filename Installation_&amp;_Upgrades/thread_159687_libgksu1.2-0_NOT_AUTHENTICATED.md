---
title: "libgksu1.2-0 NOT AUTHENTICATED"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by WrathofthePenguin on 2006-04-13
This morning when I brought up my system I found that there were updates available. There were four updates available, one of which was:

libgksu1.2-0 (library providing su and sudo functionality), new version 1.3.1-1ubuntu7

However, when I went to install these updates, the Summary page warns me that this update is "NOT AUTHENICATED", and "doing this could allow a malicious individual to damage or take control of your system."

Now, being a naturally paranoid individual, I am suspicious. I do not like seeing that an update that deals with SU and SUDO functionality is not authenticated. I also do not like that nobody else is questioning this in the forums (at least that I can find), which might just mean that I am incompetent (a distinct possibility), that I am the only one getting this message, or that nobody cares about security (which I doubt).

So, is this a known problem, or is somebody out there playing games?

---

### Post by mandrakethepenguin on 2006-04-13
Nobody is playing games, I downloaded the same update.  Its basically saying that its downloading the update from a non-official-ubuntu source.  If you have overwritten your sources.list manually or have used automatix, you may see these  'warnings' when installing software with apt-get or Synaptic.

---

### Post by WrathofthePenguin on 2006-04-13
[QUOTE=mandrakethepenguin]Nobody is playing games, I downloaded the same update.  Its basically saying that its downloading the update from a non-official-ubuntu source.  If you have overwritten your sources.list manually or have used automatix, you may see these  'warnings' when installing software with apt-get or Synaptic.[/QUOTE]

Ok, now I'm a little more disturbed. I was aware of what you wrote about here, but I haven't gotten "Not Authenticated" errors when updating other packages from non-Officially supported repositories. So I went in and disabled all repositories except for the Officially Supported ones, and did an apt-get install update, then ran the updater again. This time I didn't get the error, although the same update was listed and installed. This raises a couple of questions: Was the Synaptic Package Manager ready to download the update from an non-official repository over an Official one? Are they available on both, and are they they same?

Just so you understand why I am worried about this, look at this link:

[http://www.openssh.com/txt/trojan.adv](http://www.openssh.com/txt/trojan.adv)

It can happen, and when I get a message which makes me question the authenticity of an update, especially one for SU and SUDO, I feel it's best to not update until I'm sure.

---

### Post by towsonu2003 on 2006-04-13
I too get those errors, only when I am upgrading without first updating. I think your problem wasn't related to un-official repositories, and it got resolved by doing sudo apt-get update again...

---

### Post by WrathofthePenguin on 2006-04-13
[QUOTE=towsonu2003]I too get those errors, only when I am upgrading without first updating. I think your problem wasn't related to un-official repositories, and it got resolved by doing sudo apt-get update again...[/QUOTE]


mandrakethepenguin and towsonu2003, I want to make sure I thank both of you for your answers. I'm going to try to find out exactly what causes the "Not Authenticated" message, if only for my own curiosity.

---

### Post by DarkMageZ on 2006-04-17
"NOT AUTHENTICATED" means that the package was not signed using any of the GPG keys that ubuntu or you have provided to apt.

if the package came from the offical repository's, then either someone is playing with you, or someone isn't following procedure.

considering the low number of replies to this, i'm going to presume that there was a unsigned package on the server for afew minutes, and it was quickly noticed and fixed.

When you get "NOT AUTHENTICATED" it is allways recommended to take a careful look at where the packages REALLY came from. Like i said before, if it came from the offical repository's then something is wrong.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=DarkMageZ]"NOT AUTHENTICATED" means that the package was not signed using any of the GPG keys that ubuntu or you have provided to apt.

if the package came from the offical repository's, then either someone is playing with you, or someone isn't following procedure.

considering the low number of replies to this, i'm going to presume that there was a unsigned package on the server for afew minutes, and it was quickly noticed and fixed.

When you get "NOT AUTHENTICATED" it is allways recommended to take a careful look at where the packages REALLY came from. Like i said before, if it came from the offical repository's then something is wrong.[/QUOTE]
there is one more possibility: when I do not refresh my apt-get for a while (more than 24 hours) while update-manager has "update available" notification up (red arrow thingy), and than try to update, it will show "NOT AUTHENTICATED". If a reload/refresh my apt-get list (sudo apt-get update), the "NOT AUTHENTICATED" will disappear.

---

