---
title: "Laptop Wireless did not work after  Ubuntu 10.04 installation."
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by dmp2010 on 2010-09-28
I installed the Ubuntu 10.04 on my old Compaq v2000 but the Internet did not work so I installed the win7.

---

### Post by guntu on 2010-09-29
[FONT=Arial][FONT=&quot]> **dmp2010 said:**
> I installed the Ubuntu 10.04 on my old Compaq v2000 but the Internet did not work so I installed the win7.

Hi, 
I had t he same problem - first when I installed Ubuntu in my Compaq latop and then on my HP Pavillion DV2000.  I struggled quite a lot to find information to make the wireless work but it's actually quite simply.  Follow these steps: 

After you have install Ubuntu, make sure you have an internet connection by connecting directly with a DSL cable from your computer to your modem. 

1) Log in to Ubuntu
2) Open the "Synaptic" 
**    System** > **Administration** > "**Synaptic Package Manager**"
3) Click on "Reload".  When finished,
4) Click "Mark All Upgrades". When finished,
5) Click "Apply".  Wait for the programme to finish installing all the updates. Then,
6) Restart your computer.
7) Open Synaptic again. 
8) In the search window, type: bcmwl-kernel-source
9)  a) If it's not found, then you need to download it and install it. Here's how:
        1) Go to : [http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)
        2) Choose your architecture: amd64 or i386 .  My HP Pavillion dv2000 laptop is amd64 - FYI. 
        3) Select a server near you. I'm in Europe so I chose the one from France. 
        4) Download it.
        5) Navigate to the folder where you saved the file to.
        6) Double click on it and it will install it for you. 

    b- If it finds it, right click on it (bcmwl-kernel-source) and if you see the option to update it "Mark for update", then selected and then click on "Apply" to update it. 
    b- It it finds it but you can't select "update", that's fine, that means you have the lattest version. Simply close the window. 

10) Open "Hardware Drivers". **System** > **Administration** > "[B]Hardware Drivers"
[/B]11) If you see that the " Broadcom STA proprietary wireless driver" wireless driver is installed (active), click on it and click on "Remove". When finished, [/FONT][/FONT]
  [FONT=Arial][FONT=&quot]12) Locate the driver called "Broadcome 43 wireless driver" and click on "Activate".
12) Once it's finished installing this driver, you should see the wireless networks available around you when clicking on the wireless icon on the top bar. 

And that's it!  

If you run into any trouble, just send me a message. I know how frustrating it can be not to be able to make your wireless work but once you get it to work, you can enjoy Ubuntu and it's very well worth it!!  Don't give up! 
[/FONT][/FONT]

---

### Post by dmp2010 on 2010-10-03
Thanks buddy, it worked.

---

### Post by Bandit2003 on 2011-01-26
Followed instructions as posted, but when i went to Hardware drivers to locate it was not there.

Any thoughts?

---

### Post by fallenstar on 2011-02-13
> **Bandit2003 said:**
> Followed instructions as posted, but when i went to Hardware drivers to locate it was not there.

Any thoughts?

go into synaptic package manger and type into the search box "bcm". that should bring up broadcom packages, including the STA packages and the b43 firmware cutter. 

Install them all (should be five) and you will have at least the STA driver in "hardware drivers", and possibly the b43 also.

---

### Post by fallenstar on 2011-02-13
:confused:
I have only the STA visible in "Hardware Drivers" which worked fine in 10.10, but won't activate now in 10.04. I've tried installing only the b43, then only the STA, then both, restarted it several times (worked last time) but nada...? :KS

any thoughts?

---

