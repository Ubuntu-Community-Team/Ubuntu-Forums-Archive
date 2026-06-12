---
title: "Lucid Lynx ON VirtualBox"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by _elgato on 2010-03-23
Hey fellas, I was trying to install the beta (yes I know it's a beta and that it could not run on all computers) and I was wondering if any of you guys could make it run on VirtualBox under Win7 or any other Win OSes. Maybe it's just a Win7 problem.

Thanks

---

### Post by Whisp3r on 2010-03-23
> **_elgato said:**
> Hey fellas, I was trying to install the beta (yes I know it's a beta and that it could not run on all computers) and I was wondering if any of you guys could make it run on VirtualBox under Win7 or any other Win OSes. Maybe it's just a Win7 problem.

Thanks

I have tried running it under Virtual Box. It goes to the splash screen, I choose to boot it, and all I get is a black screen with a cursor.

---

### Post by hourna on 2010-03-23
i had it running smoothly. however i was not able to change the resolution. i tried installing guest additions. however it did not work. after guest additions installation i rebooted and X failed. in karmic, i could change the resolution after guest additions installation.

---

### Post by _elgato on 2010-03-25
> **Whisp3r said:**
> I have tried running it under Virtual Box. It goes to the splash screen, I choose to boot it, and all I get is a black screen with a cursor.

I have the exact same problem so I won't try to install it anymore.

Thanks, guys

---

### Post by Locke2053 on 2010-03-25
I was able to get Ubuntu to install on VirtualBox by disabling the network adapter. Unfortunately, everything went to hell after installing the VBox "Guest Additions" drivers. I tried with 64 and 32 bit. I tried with the "Beta 1" iso and a nightly iso.

Conclusion: Lucid Lynx 10.04 just does not work on VirtualBox.

---

### Post by bluelamp999 on 2010-03-25
I gave up too. Installing VBox Guest Additions b0rks the whole thing...

I doubt that it's worth posting a bug report though as it is a Beta.

---

### Post by coffeecat on 2010-03-25
> **Locke2053 said:**
> Conclusion: Lucid Lynx 10.04 just does not work on VirtualBox.

**[SIZE=4]...yet.[/SIZE]**

There. Fixed that for you. :wink:

Running as a guest OS in VirtualBox is too important to be neglected. Let's hope it will work by final. Either Jaunty or Karmic - I can't remember which - was hell in VirtualBox around the Beta stage but worked by the time of final.

---

### Post by Ibidem on 2010-03-25
Beta is the best time for reporting bugs.
The report should be a bug in Guest Additions, not the main system...

---

### Post by KdotJ on 2010-03-25
I managed to get Lucid to work finr using VMware in Windows 7. I havent actually tried on VirtualBox....

---

### Post by cosine352 on 2010-03-25
I mannaged it to work after disabling the ACPI

---

### Post by xebian on 2010-03-25
You can get VBox 3.1.6 now has the fix

---

### Post by dazvansgillio on 2010-03-25
Try this link     [http://maxolasersquad.blogspot.com/2010/03/ubuntu-1004-lucid-lynx-alpha-in.html](http://maxolasersquad.blogspot.com/2010/03/ubuntu-1004-lucid-lynx-alpha-in.html)      - it worked for me. Check out the links at the bottom of the page on this link for a bit more info.

---

### Post by xebian on 2010-03-25
3.1.6 now has the seamless mouse integration working with Lucid guest as well as the screen resolution.

---

### Post by Sensiva on 2010-03-26
for those who doesn't have the ability to upgrade to 3.1.6, I tried the instructions in the page posted by [dazvansgillio]("http://ubuntuforums.org/member.php?u=839119") [http://maxolasersquad.blogspot.com/2010/03/ubuntu-1004-lucid-lynx-alpha-in.html](http://maxolasersquad.blogspot.com/2010/03/ubuntu-1004-lucid-lynx-alpha-in.html), worked fine, except that compiz is painfully slow. Well it has been always slow, but after applying this patch it became unbearable.

I hope this helps, happy testing. Thanks for sharing.

/Sensiva>

---

### Post by bluelamp999 on 2010-03-26
> **xebian said:**
> 3.1.6 now has the seamless mouse integration working with Lucid guest as well as the screen resolution.

Can confirm this. Well done VirtualBox!

Back to testing...

---

