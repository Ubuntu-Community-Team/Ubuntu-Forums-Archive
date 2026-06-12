---
title: "ATI Drivers - Suspend/Hibernate Problem"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by m i k e on 2008-01-05
I have clean install of Gusty 7.10 and an ATI Radeon 9800 Pro.  I installed the proprietary driver via the "Restricted Drivers" window in Ubuntu.  Apparently the new ATI drivers (7.12) fixed the suspend/hibernate issue according to: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Suspend.2FHibernation_work_with_7.12](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Suspend.2FHibernation_work_with_7.12) However, I still cannot suspend or hibernate successfully.  I installed the drivers through Ubuntu just a few days ago, well after ATI released their update.  Is is possible that I didn't get the latest version of the drivers?  Does anyone know how to fix this issue?

---

### Post by esteckis on 2008-01-05
I am a linux newbie, what I did is use the New ENVY version to install latest ATI update and the driver installed and Compiz works. ATI's latest driver is dated 12/20/07.  Now the envy program is supposed to check your system and download the correct ATI driver from ATI's site (this way you are getting the most current driver).

Envy site  [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Now I downloaded the Envy DEB and Ubuntu has a Debian installer which handled the installation. Just double check ATI's site that they have a compatible Linux driver for your video card and Envy should get it ok. I am using the ATI 1250 series onboard video.

For me, I do have screen saver flickering and full screen video flickering with the new ATI driver. But it is better then having my system reboot whenever an opengl screensaver started with the older ati driver.

---

### Post by z-itou16 on 2008-01-06
thanks esteckis for the info. i totally forgot about this, i heard this before. i have about 3 months experimenting with linux and i love it. this gutsy makes thing easier. 

now installing the Ati driver couldnt solve my issue for either hibernate nor suspend. I had the ati driver installed before but using the restricted driver in ubuntu. the diference with that vs envy is that envy give you the update one plus compiz enable. The prob is when the fglrx installed hibernate goes to black screen and thats it, it halted there for >20mins and nothing happens, the same with suspend. 

not sure what to do, ill look for more info and if anything i got solve here i will post it here if there is no solution at that point.

thank you anyways

---

### Post by Partyboi2 on 2008-01-06
There is a known bug for laptops regarding the  suspend issue and a workaround
[http://ubuntuforums.org/showthread.php?t=588239](http://ubuntuforums.org/showthread.php?t=588239)

---

### Post by Chete on 2008-04-07
I have exactly the same problem withGutsy 7.10 running in a Dell Inspiron 9200 with ATI Mobility Radeon 9600. After reading tons of posts about the topic and spend hours and hours of testing I get the following conclusions:

[LIST]
[*] Suspend/hibernate works pretty well in my Inspiron+ATI with the Ati open source driver, no changes needed.

[*] Suspend/hibernate works with the latest Ati driver (version 8.3) in my system but with some tricks and restrictions.
[INDENT][LIST]
[*] I have installed the latest driver manually and I did not use the restricted drivers. There is a nice step-by-step description in [this web]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts").
[*] I have edited the /etc/default/acpi-support and added  fglrx to the MODULES="". The system will unload the graphic module before hibernate and load it again after you resume. Without this, my system does not hibernate.
[*] I can not hibernate if I am running compiz. After Compiz is disabled (System > Preferences > Appearance > Visual effects tabs > none) + reboot, the system is able to hibernate. Disabling compiz on the fly with metacity --replace does not work for me. 
[/LIST][/INDENT]
 
[*] I did not manage to suspend/hibernate while using the restricted driver, but I did not try to add fglrx to the MODULES line. Maybe this will work.
[/LIST]

I have found other issues. For example, if you have been playing with the uswsusp package, check that the syntax of the s2disk command is consistent with the one in the /etc/acpi/hibernate.sh script (see [this bug]("https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/109151")). I had to change the following line in my /etc/acpi/hibernate.sh:

        #/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
        /sbin/s2disk -r  $DEVICE

---

