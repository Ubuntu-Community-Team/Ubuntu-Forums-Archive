---
title: "Nvidia Driver and Secure Boot"
date: 2017-08-26
forum: Installation &amp; Upgrades
---

### Post by admiralspeedy on 2017-08-26
Ok, so I'm having a weird issue right now and could really use some help. I will start with some backstory to explain the entire issue:

I only use Linux for building Android, so rather than dealing with setting up a dual boot system (since I already had Windows 10 installed) I took an extra hard drive I had sitting around and installed Xubuntu on it, popped it in my PC and whenever I wanted to go do a new build of Android for my phone I would simply turn off my PC, pop the side off my case (it's right next to me), disconnect my Windows SSD and connect the Linux drive and then turn it back on and it would boot to Xubuntu totally fine. This however has gotten a bit annoying and I need that drive for another purpose now, so I bought new 2TB drive for Xubuntu to permanently leave connected (The drive I have Xubuntu on is way smaller and more suited to the other purpose I have for it, which is why I'm not just using the new drive for that purpose instead) and basically I was just going to make sure the boot order list in my UEFI/BIOS would always boot Windows first and then I would just override this from the boot menu when I wanted to boot Linux. Please do not suggest setting up a proper GRUB dual boot unless it will actually help in some way, because that is not what I'm asking about.

Now, I wanted to do a clean install of 16.04 LTS to this new 2TB drive but I remembered how much of hassle it was to install it before because the default graphics driver does not work at all with my GTX 970, I just get artifacts or a black screen when I try to boot the installer or the installed OS without nomodeset, until I install the Nvidia driver, which is where my issue begins. I use Secure Boot and I know it says you have to turn off Secure Boot to use proprietary drivers, however on my old installation on the other drive I have no clue how I managed to do it (I remember trying various combinations of installing with and without Secure Boot enabled) but the Nvidia driver works fine on it with Secure Boot on, but no matter what I do on the new installation as soon as I re-enable Secure Boot the Nvidia driver seems to only be working partially. By partially I mean that I can still actually boot into Xubuntu (whereas with the default driver enabled I cannot) and my resolution is correct, but my second monitor no longer functions and when I open up the Nvidia driver settings application almost everything is missing out of it as if it's not fully initialized or something.

Does anyone have any clue why it would work with Secure Boot enabled on one installation and not the other? I've been looking into ways of signing the driver myself but I'm a bit lost there and I know I didn't do that before so I really don't understand why it works on my old installation and I also don't understand why it seems to still work partially with Secure Boot enabled on the new installation.

---

### Post by ubfan1 on 2017-08-26
I understand the 16.04 + releases did tighten up the requirement that  modules are signed also, so that's the root of your problem.  Before this, that wasn't enforced.  Now how the old 16.04 boots, I'd guess you have an old grub install on that disk, which doesn't check as fully as a newer grub.  Maybe try installing that version of grub on your new disk?  Check what's really running with lshw -c video and see if it's the nvidia driver.  I don't see how it can partially run either, so maybe it's another driver which is actually running.

---

### Post by admiralspeedy on 2017-08-26
That's the thing. I used the exact same installation media to do this new install, the USB drive I made for the original install. Also, I had this same issue with that original install and after reinstalling many times and toggling Secure Boot many times it eventually just worked but I couldn't recreate that this time. I will check what is running though, because maybe it is running the default driver and it just happens to work because the Nvidia driver set the correct resolution or something like that.

I just gave in and disabled it when prompted because I didn't realize it doesn't force me to turn it off in the UEFI but rather does some shim thing with GRUB and I don't really care if my Xubuntu install boots in insecure mode since I don't even use it very often.

---

