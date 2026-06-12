---
title: "How do I install the Flash plugin to work with Firefox 4RC on Ubuntu?"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by dbhatt on 2011-03-17
I just downloaded the RC for Firefox 4, and for some reason I can't install the Flash Plugin for it. I tried going to the Adobe website and manually downloading and installing it, but I don't know how to run .rpm files/what to do after extracting the tar files. I decided to uninstall and then reinstall the plugin from the shell, and it didn't make a difference. I'm at a loss as to what I should do next, especially since Flash is already installed and works with my Firefox 3.6.15 build.

Could someone suggest something?

---

### Post by runeh76 on 2011-03-17
What is RC?

---

### Post by dbhatt on 2011-03-17
> **runeh76 said:**
> What is RC?

Stands for Release Candidate. Firefox 4 hasn't officially been released, but the version of the code that Mozilla plans on releasing bas been released. This is called the RC and its usually the case that there are only minor differences between the RC and the final build.

---

### Post by runeh76 on 2011-03-17
Oh okey,thx for the info! So whats ur problem, and what u need to do?

---

### Post by dbhatt on 2011-03-17
I explained in the original question. I'm trying to get the Flash Player plugin work with Firefox 4 and I'm not sure how to do that.

---

### Post by mikewhatever on 2011-03-17
I didn't have to do anything at all to make flash work with Firefox4, it just did. By the way, it's the 32bit adobe flash plugin from the repositories.

---

### Post by dbhatt on 2011-03-17
> By the way, it's the 32bit adobe flash plugin from the repositories.

Could you tell me where you got it from/how you installed it? I was trying to download it from the Adobe website, instead of using Linux repositories.

---

### Post by runeh76 on 2011-03-17
First..do u have 32/64b Ubuntu?
Second..Use Chromium  :)

---

### Post by dbhatt on 2011-03-17
I found the solution. 

Firefox 4 has an extension called FlashAid which removes conflicting version of Flash and installs the correct and latest version based on the system architecture. It runs a shell script and needs sudo access, but I read through the commands and they seem to be non-malicious. I also ran it and Flash now seems to work fine with Firefox 4. The addon also notifies you about updates, which is kinda sick.

---

### Post by wojox on 2011-03-17
> **dbhatt said:**
> I found the solution. 

Firefox 4 has an extension called FlashAid which removes conflicting version of Flash and installs the correct and latest version based on the system architecture. It runs a shell script and needs sudo access, but I read through the commands and they seem to be non-malicious. I also ran it and Flash now seems to work fine with Firefox 4. The addon also notifies you about updates, which is kinda sick.

Yes the guy who wrote that is a member here, lovinglinux.

---

### Post by dbhatt on 2011-03-17
That's pretty cool. AdBlock still doesn't work with Firefox 4 though, which is annoying.

---

