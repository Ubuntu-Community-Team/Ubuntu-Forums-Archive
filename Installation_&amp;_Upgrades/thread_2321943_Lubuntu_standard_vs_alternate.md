---
title: "Lubuntu: standard vs alternate"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2016-04-25
Hi,
I have a set of old PC with pentium 4 and 512 MB of RAM :(
I migrated these PC from windows xp to lubuntu 14.04 LTS 32 bit. Unfortunately they are very slow especially in online navigation task and this was expected by reading systems requirements [here]("http://lubuntu.net/"). I'm using both firefox and qupzilla.
I know the existence of alternate version especially devised for old PC. So, in the past the minimum requirements of RAM recommended to install the alternate version was below 384 MB while now it is below 700 MB [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO).
I know that the alternate installation process uses  simpler graphics. However, during the normal use, is there any advantage about using alternate version? If yes, how can I switch to this version without reinstalling the OS from scratch?
Do you recommend to upgrade to 16.04?
Thank you

---

### Post by RobGoss on 2016-04-25
If your machines are old and do not have much Ram or have a slow processor you might try a lighter distribution. There are many that might fix your specs.

Lubuntu, Kubuntu, Xubuntu, are lighter them most distributions

---

### Post by erotavlas on 2016-04-25
> **RobGoss said:**
> If your machines are old and do not have much Ram or have a slow processor you might try a lighter distribution. There are many that might fix your specs.

Lubuntu, Kubuntu, Xubuntu, are lighter them most distributions

Ok, thank you for your reply. However, you do not answered to my question. I know that there are several [lightweight distributions.]("https://en.wikipedia.org/wiki/Lightweight_Linux_distribution")

---

### Post by grahammechanical on 2016-04-25
The usefulness of the Alternate ISO image comes from the fact that it uses a text based installer. And so, it not only requires less RAM during installation but also works with less powerful video adapters.

It does not install a text based version of Lubuntu. It will install the same Lubuntu desktop as in a standard Lubuntu ISO image. It seems that the standard GUI installer requires more RAM during the installation process than the desktop & user interface requires after installation

The effect that you are experiencing is down to the low capabilities of the video adapter and the very high expectation of certain web sites. Especially those that embed video files into the web page as advertising, I have found that some national newspaper web sites have more advertising than news content and that simply scrolling down the page becomes next to impossible on my machine even though I have twice the RAM, a dual core CPU and a video adapter with 1 GB video memory than you do.

Regards.

---

### Post by erotavlas on 2016-04-25
> **grahammechanical said:**
> The usefulness of the Alternate ISO image comes from the fact that it uses a text based installer. And so, it not only requires less RAM during installation but also works with less powerful video adapters.

It does not install a text based version of Lubuntu. It will install the same Lubuntu desktop as in a standard Lubuntu ISO image. It seems that the standard GUI installer requires more RAM during the installation process than the desktop & user interface requires after installation

The effect that you are experiencing is down to the low capabilities of the video adapter and the very high expectation of certain web sites. Especially those that embed video files into the web page as advertising, I have found that some national newspaper web sites have more advertising than news content and that simply scrolling down the page becomes next to impossible on my machine even though I have twice the RAM, a dual core CPU and a video adapter with 1 GB video memory than you do.

Regards.

Ok, so do you suggest? Is there any other distribution better suited for my purposes (preferably debian based)? Or is lubuntu the best?
Thank you

---

### Post by RobGoss on 2016-04-25
> **erotavlas said:**
> Hi,
I have a set of old PC with pentium 4 and 512 MB of RAM :(
I migrated these PC from windows xp to lubuntu 14.04 LTS 32 bit. Unfortunately they are very slow especially in online navigation task and this was expected by reading systems requirements [here]("http://lubuntu.net/"). I'm using both firefox and qupzilla.
I know the existence of alternate version especially devised for old PC. So, in the past the minimum requirements of RAM recommended to install the alternate version was below 384 MB while now it is below 700 MB [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO).
I know that the alternate installation process uses  simpler graphics. However, during the normal use, is there any advantage about using alternate version? If yes, how can I switch to this version without reinstalling the OS from scratch?
Do you recommend to upgrade to 16.04?
Thank you

> how can I switch to this version without reinstalling the OS from scratch?

I'm not really sure what you mean by switching versions, are you asking to switch from 14.04 To 16.04? , if this the case and 14.04 is the only OS you have on that machine you can choose to Wipe the disk and install 16.04.

But I have to advise you if this is a old machine and does not have the requirements to run 16.04 it will not be a smooth installation and it will not preform well.

---

### Post by Hedon James on 2016-04-25
> **erotavlas said:**
> Ok, so do you suggest? Is there any other distribution better suited for my purposes (preferably debian based)? Or is lubuntu the best?
Thank you

I am a fan of Ubuntu, especially the LXDE desktop, but nearly every OS adds newer features over time, gradually increasing the software "draw" on system resources.  IMO, Lubuntu has exceeded your hardware.  It will run, and maybe even run "fine", but it will become more and more restrained over time.  Is there another distro better suited for your purposes?  IMO...yes, but only YOU can answer that question, based on your needs and preferences.  Based on your OP, and your hardware specs, I might suggest that AntiX is a better OS for that particular machine.

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

Stick with the main "AntiX" selections, not the "MX" selections, as the MX distro uses an XFCE desktop environment, which is actually slightly heavier than the LXDE in Lubuntu.  AntiX uses the Fluxbox or IceWM window managers and are significantly lighter on resources.  And AntiX does a great job with "polish" of such a minimal distro, IMO.

If AntiX doesn't do it for ya, check out distros with OpenBox, FluxBox, and or IceWM desktops...like CrunchBang, SparkyLinux(?), SalentOS, etc...  Good luck!

---

### Post by mörgæs on 2016-04-26
There are many light distros to choose from but it does not matter that much. What adds to the workload is not the operative system but first of all the browser, as explained in post #4.

I suggest that you try a variety of lightweight browsers, among others **links2**. It takes some time to get used to the keyboard shortcuts and mouse gestures but I recommend it none the less for reading web sites (for sites where you need to post a more advanced browser is necessary). With links2 512 MB will be plenty.

---

