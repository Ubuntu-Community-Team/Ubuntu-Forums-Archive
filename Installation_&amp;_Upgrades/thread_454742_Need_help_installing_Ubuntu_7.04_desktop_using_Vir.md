---
title: "Need help installing Ubuntu 7.04 desktop using Virtual Server 2005 R2"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by Kandamer on 2007-05-25
I have been trying for days to get Ubunto 7.04 Desktop to install under Microsoft Virtual Server 2005 R2 to no avail.

My problem is that during the install Ubunto switches to a video mode that is not supported so I can not see to finish the install.

I have tried pressing F4 and selecting 800x600x16 but it still changes to something I can not see.

I have also tried booting it with the safe graphics mode and it will boot up into the GUI where I should be able to select "Install" from and continue but after the GUI comes up the keyboard and mouse do not function.

Any help would be greatly appreciated.

Thank you.

---

### Post by globalmcs on 2007-05-29
Were you able to install it ? I just tried and had the same problem you did.
I may try with Virtual PC and if it works I'll transfer the virtual hard drive over to the Virtual Server.

---

### Post by regomodo on 2007-05-29
Have you tried Virtualbox? I'm guessing you are virtualising.

It's free and a small download

[http://www.virtualbox.org](http://www.virtualbox.org)

---

### Post by Kandamer on 2007-05-29
I was not able to install it under Virtual Server 2005 because of the video issue, but I was able to get it to work just fine with our version of VMware workstation.

We use both here at the office and I just wanted to get it to work on both platforms.

globalmcs if you have success with the transfer from vpc let me know :)

I will also look into the Virtualbox package.

Thanks

---

### Post by cknight725 on 2007-06-25
Had the same trouble:

1. Boot from Ubuntu’s install CD
2. Press F4, then choose “1024×768 16&#8243;
3. Then press F6, and at the end of the line add this: text vga=0×314

Worked great for me!

---

