---
title: "[Ubuntu] Unable to install"
date: 2024-11-23
forum: Installation &amp; Upgrades
---

### Post by nickleclair on 2024-11-23
Running into a weird issue I have never encountered before.

Trying to install Ubuntu 24.10 and 24.04.1 but encountering an issue.  I tried imaging a usb drive multiple times and buying a new usb drive just to be certain it wasn't a usb drive issue.

I am able to boot into the USB drive without any programs.  But when I click "Try and Install Ubuntu" it loads into a blank screen.  I can hear audio as if something is happening but nothing ever loads onto the screen.  I also tried Ubuntu (Safe Graphics) options but nothing loads there either.

I am running Asus B650 Plus, AMD 7800X3D and AMD 7900XTX for my understanding there should be no issues with the hardware I am using.  Has anyone encountered this issue and was able to resolve it?  I am trying to setup a dual boot with Windows 11 pro.

---

### Post by Rubi1200 on 2024-11-23
Have you tried disabling Fast Startup, Secure Boot, and TPM before booting with the USB?

What graphics card do you have installed?

---

### Post by yancek on 2024-11-23
In addition to answering the questions in post 2, did you verify the iso was not corrupted during the download process?

[https://ubuntu.com/tutorials/how-to-verify-ubuntu#3-download-checksums-and-signatures](https://ubuntu.com/tutorials/how-to-verify-ubuntu#3-download-checksums-and-signatures)

---

### Post by nickleclair on 2024-11-24
My GPU is 7900XTX, I tried disabling Secure boot no luck.  I can boot into the USB drive no problem it just always fails to load once I click an option. Also tried installing it etcher and rufus but neither worked.  Have downloaded ubuntu multiple times (24.10, 24.04).  Might try bumping myself down 23 and see if that ISO works.  I'll try without TPM.  I haven't tried that yet.

---

### Post by tea for one on 2024-11-24
Is the information here any help?
[https://askubuntu.com/questions/1513117/no-gpu-output-with-dedicated-amd-7900xt-on-ubuntu-24-04](https://askubuntu.com/questions/1513117/no-gpu-output-with-dedicated-amd-7900xt-on-ubuntu-24-04)

---

### Post by yancek on 2024-11-24
You were asked in post 2 what graphics card you have but did not answer that?  Might be helpful.
 If you have downloaded different Ubuntu iso files it is not likely that they were all corrupted and this does not happen often but is simple to verify.
Have you tried booting from different usb ports?

>  Might try bumping myself down 23 

The above quote is from your post 4, don't do that as it is out of support.  If you want an earlier version, try 22.04.

>  
I am able to boot into the USB drive without any programs.

What does that mean?  That you simply get a black screen and can't access anything.  I'd think your problem is likely related to graphics.
Do you get this same problem when you write the iso to the usb with Etcher, Rufus and whatever other software you use?

---

### Post by nickleclair on 2024-11-24
I posted the graphic card and CPU in my original post and in my reply "AMD 7900XTX".  I also posted my motherboard and CPU in the original post.

[COLOR=#000000][INDENT]I am running Asus B650 Plus, AMD 7800X3D and AMD 7900XTX for my understanding there should be no issues with the hardware I am using. Has anyone encountered this issue and was able to resolve it? I am trying to setup a dual boot with Windows 11 pro.[/INDENT]


[/COLOR]

---

### Post by nickleclair on 2024-11-25
I can load into the menu options for the usb drive after booting into the drive.  But once I click any of the options nothing effectively loads (try and install, Ubuntu (safe graphics), UEFI).  I do hear a sound as if something is happening but I don't see anything on my screen.  It's just grayed out.

---

### Post by oldfred on 2024-11-25
Have you updated UEFI & SSD firmware to latest available?

---

### Post by nickleclair on 2024-12-10
I also tried Fedora to rule out an Ubuntu-specific issue, but the problem persisted. Ultimately, updating the BIOS resolved the issue, allowing me to successfully install Ubuntu.

---

### Post by ActionParsnip on 2024-12-12
Please mark as solved if there is no more issue

---

