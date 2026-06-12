---
title: "Installed a dependency of 'ia32-libs'"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by Rainbowdashepicness on 2012-10-16
Alright, so I'm not new to Linux, whilist I'm still learning, although who isn't? So, I wanted to install Skype, complained about not being able to be installed due to 'ia32-libs' not being installed, so i said fine... and I go to install it via terminal, I enter 'sudo apt-get install ias32-libs' and then it tells me it requires 'ia32-libs-multilarch' so i do the same for that, only this time it shoots out a bunch of packages it depends on; so I'm say what the hell. If I was thinking I wouldn't have done what i did next, I decided to install each dependence one by one, I start with 'libgl1-mesa-dri:i386' after doing that I go watch a youtube video, it's only then that applications start removing themselves, then chrome closes. I look at terminal, and it shows 'removing (application-name)' for all the applications that are run for Linux. Then terminal closes and unity. I'm left with a blank desktop. I reboot, hoping that might solve something; no, I'm stuck on Ubuntu's kernel. I can enter commands via that, but can't get internet access. Any help would be appreciated, thanks.

---

### Post by Rainbowdashepicness on 2012-10-16
Also, boot logo does NOT show. Just black, then a prompt comes up.
```

RAINBOWDASHL-PC$~ LOGIN: rainbowdash
PASSWORD: ***
```
Then goes on too tell me the last time I logged in.

---

### Post by SlugSlug on 2012-10-16
Not sure what you done there.

login at command prompt and try 

```
 sudo apt-get --reinstall install ubuntu-desktop
```

if that errors try 

```
sudo apt-get install ubuntu-desktop 
```

---

### Post by Rainbowdashepicness on 2012-10-16
All those 2 commands do is list a whole bunch of packages, then say they need to be downloaded. At this point in time I only have Wi-Fi and my drivers are proprietary, so they aren't installed.

---

### Post by SlugSlug on 2012-10-16
Your going to need to connect a network cable, other option is boot live cd and mess around a fair bit

---

### Post by Rainbowdashepicness on 2012-10-16
Ok, I do have a Live CD available, (I have like 3 OS's on my FLash Drive), so I'm able too boot off of that. Do you have anywhere I can start? Or should I just reinstall the OS.

---

### Post by SlugSlug on 2012-10-16
I've never used this but... do you have the CD rom you used to install your current distro?

[https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

---

### Post by Rainbowdashepicness on 2012-10-16
> **SlugSlug said:**
> I've never used this but... do you have the CD rom you used to install your current distro?

[https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

Yes, I do.

---

