---
title: "NEED HELP FAST!!! cant install ubuntu"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by jnedenrod on 2012-07-21
i'm using Win7 64-bit
HP laptop
 
Does the laptop need to be working normally before I can install ubuntu?  it turns on and goes to a blue background with a moveable mouse pointer, and that's it.
 
i got a short dst failed message. i'm not sure if my hard drive isn't working because of a trojan (Norton said it fixed it) or because the laptop took a small bump. i downloaded unetbootin-windows-578 to unpack ubuntu-12.04-desktop-amd64 onto a flash drive. I put the flash drive in my computer and I get the same thing as i did without the ubuntu flash drive--asking to repair or boot normally.
 
Does the flash drive have to be blank? do i need to put the unpacked files into a folder? i'm good with computers but i'm not an expert on the BIOS. date and time are correct and i put the flash drive as the first bootup option. am i missing something?
 
With or without ubuntu, will i be able to do anything if i can get my hands on a Win7 boot disk? would that have to be a 64-bit disk?

---

### Post by darkod on 2012-07-21
When running the unetbootin procedure watch out whteher it says the bootloader was installed correctly or not. Sounds like it's not booting from the stick.

In win7, I think it's best not to double click on unetbootin when you start it, but instead to do right-click, Run As Administrator.

Before that, format the stick as FAT32.

PS. If unetbootin continued giving you trouble, try it with universal usb installer. It's free, you can find it on google.

---

### Post by papibe on 2012-07-21
Hi jnedenrod. Welcome to the forums ):P

Sorry to hear that.

A few ideas:

Try going into the BIOS and do the hard disk diagnostic. 

Boot into your Windows Restore/Rescue CD and do chkdsk?

Regards.

---

### Post by jnedenrod on 2012-07-23
> **darkod said:**
> When running the unetbootin procedure watch out whteher it says the bootloader was installed correctly or not. Sounds like it's not booting from the stick.

In win7, I think it's best not to double click on unetbootin when you start it, but instead to do right-click, Run As Administrator.

Before that, format the stick as FAT32.

PS. If unetbootin continued giving you trouble, try it with universal usb installer. It's free, you can find it on google.

I tried installing it from a public library computer, and because it restricts access to some of the system, I had no choice but to right click and run as admin. When I installed, I remember it saying that it didn't install correctly, but I figured it was because the computer was telling me that it wasn't on the C: drive. Can I install it from a public computer as described? If so I'll be headed to the library shortly to give it a go, and I'll post what my results are.

---

### Post by darkod on 2012-07-23
> **jnedenrod said:**
> I tried installing it from a public library computer, and because it restricts access to some of the system, I had no choice but to right click and run as admin. When I installed, I remember it saying that it didn't install correctly, but I figured it was because the computer was telling me that it wasn't on the C: drive. Can I install it from a public computer as described? If so I'll be headed to the library shortly to give it a go, and I'll post what my results are.

That would depend on any security that might be implemented on public computers. There might be big limitations on using USB sticks to prevent viruses, etc.

I think no one can tell you for sure what would or wouldn't work in that case.

---

### Post by jnedenrod on 2012-07-23
> **darkod said:**
> That would depend on any security that might be implemented on public computers. There might be big limitations on using USB sticks to prevent viruses, etc.
 
I think no one can tell you for sure what would or wouldn't work in that case.
 
I'm second-guessing the install settings I used the first time. What specific settings should I be using for NetBootIn?
 
Edit: After searching, I think I had the right settings, but how would I be able to tell if the bootloader installed correctly on the flash drive?

---

### Post by darkod on 2012-07-24
> **jnedenrod said:**
> I'm second-guessing the install settings I used the first time. What specific settings should I be using for NetBootIn?
 
Edit: After searching, I think I had the right settings, but how would I be able to tell if the bootloader installed correctly on the flash drive?

I haven't used unetbootin for a while. I think during unpacking the files and creating the usb there are messages what is it doing. You can see there when it reaches the bootloader step and whether it's successful. I even think the unetbootin window doesn't close until you close it, so the messages what was done and whether it was done successfully will stay there until you close the program.

You can test the usb in another computer too so you know whether it works on it or not.

---

### Post by jnedenrod on 2012-07-26
GOT UBUNTU WORKING!!!  The problem must have been the library computer's security settings.

1) What I don't understand is, if I can retrieve my files from the HD, why doesn't it boot?

2) The CMOS battery popped out when the laptop was bumped... Does that  info help on figuring out how to get Win7 to boot or to get the HD up  and running again?

THANKS!!!

Deus ex machina. :)

---

