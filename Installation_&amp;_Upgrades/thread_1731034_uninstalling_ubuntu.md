---
title: "uninstalling ubuntu"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by lars andersen on 2011-04-16
Hi there .

I'm new here and a total newbie to ubuntu.
I helped a friend to install Ubuntu 10.10 alongside to vista.

Now we do not know how to access the windows system which she needs for using ebanking.

Please help us. ):P

---

### Post by Dutch70 on 2011-04-16
Hi and welcome to UF

Just choose vista (loader) when the grub menu comes up, or...

You may want to start here...
[[COLOR="Red"]How to get your support questions answered as quickly as possible.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by lars andersen on 2011-04-17
> **Dutch70 said:**
> Hi and welcome to UF

Just choose vista (loader) when the grub menu comes up, or...

You may want to start here...
[[COLOR="Red"]How to get your support questions answered as quickly as possible.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

Thanks
But I'm an absolute beginner who normally works on a Mac

I've no clou at all about the grub menu or the loader. All I can do is pressing F9 to enter the BIOS setup and then I do not know what to do.

Please.

---

### Post by Dutch70 on 2011-04-17
Ok, apparently you're not seeing the grub menu. That's where you choose the OS you want to login to. 

The point of giving you that link, is that you didn't give us any info to work with. The more details you give, the more details you get. (Take that with a grain of salt, if you type to much overkill, no one will read it.)

Unfortunately choosing the "install alongside" option with version 10.10 usually messes windows up.

Although someone more experience will probably have to help with it, lets have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
If you skip this step, I doubt anyone will look at it. I only say that because so many people do.

---

### Post by lars andersen on 2011-04-18
Thank You Dutch.

It take a while before I se this computer again, but I will definitely give it a try, For now I wil just save this thread.:popcorn:

My friend may end up reinstalling Vista from the original disc.

---

### Post by Dutch70 on 2011-04-18
You're welcome
So close, yet so far :)

Hate to hear that & it's probably not necessary to reinstall and lose everything. May even be an easy fix. 
I just about guarantee you it would be easier than reinstalling windows. 

The worst of it, is that it will probably turn someone away from a really awesome & completely free operating system, programs, and community.

Best regards

---

