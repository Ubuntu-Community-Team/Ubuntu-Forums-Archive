---
title: "Cannot Install Available Update--How Come?"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by Ambimom on 2007-02-08
I was notified that there was update to linux-image-386 and linux-restricted modules-386, but they required software removal.  I was instructed to "Mark All Upgrades" in Synaptic or to run "sudo apt-get dist-upgrade" in terminal.

I did both.

Synaptic won't upgrade, insisting I need dependences, but the "dependencies" are already installed.

sudo apt-get dist-upgrade in terminal informs me that "The following packages have been kept back:  linux-image-386 and linux-restricted modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded."

Can someone explain this?  What do I need to do for this upgrade?  It drives me crazy when I see this notice each time.

---

### Post by PartisanEntity on 2007-02-08
[http://www.ubuntuforums.org/showthread.php?t=356235](http://www.ubuntuforums.org/showthread.php?t=356235)

join the club :)

---

### Post by Edho on 2007-02-08
Exact the same problem here.

Thanks.

---

### Post by Ambimom on 2007-02-08
Thanks!  I guess it'll be resolved shortly. I thought it was something I did wrong.

---

### Post by LeslieL on 2007-02-08
Me too. I fiddled around with the repositories and found it comes from the security updates repo. So I can get rid of the notice by unchecking that one - which is probably not the best thing to do, but it keeps things tidy-looking.

---

### Post by jnhea on 2007-02-09
I had the same problem and, not being very patient, I took a chance on crashing my system and just removed the existing files using the Synaptic Package Manager. 

When I marked both of them for removal and applied, it said it would also remove (I believe) linux-386. I told it to "go ahead". It did it. 

Then I checked for updates. It found some entirely unrelated to what I had done, but it did not list the ones that would replace what I had uninstalled. I updated these. Then I went back to the package manager and looked for files not installed. I found the linux-386 and marked it for installation. It came back with a message that there were some other files it needed to go with it -- I think there were 5 of them, including the other 2 that caused all this foo foo.

I told it to "go ahead" and download and install them. It did it.

I rebooted. Everything seemed OK, except it had changed the resolution of my screen to 640x480. Not what I wanted! It wouldn't let me change it. So, I crossed my fingers and rebooted again. It worked that time, and I don't see any ill effects.

Hope this helps.

jnhea

---

