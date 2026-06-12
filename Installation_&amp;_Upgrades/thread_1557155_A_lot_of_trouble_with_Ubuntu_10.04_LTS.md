---
title: "A lot of trouble with Ubuntu 10.04 LTS"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by kuramayoko10 on 2010-08-20
Hello guys,

This is my first post here in the forums, which is cool, but sadly it is to complain and ask for help.
It seems that the updgrade that I made in my ubuntu 9.10 to 10.04 turned to be a downgrade... I am having some glitches here!

First, started off that I couldn't turn off or reset my computer using the power buttons, it simply logs out.
I found a similar problem in a thread and I got this solution:
```

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

sudo update-grub                      
```Then I forced it to shut off with the command:  sudo poweroff

When I turned it on again my icons like Trash bin, Netowrk meter, Keyboard layout have disappeared from my panels... 
And it doesn't shut off anymore (it did for a couple times only).

Please help me to fix those errors.. and just to note the upgrade was successful in every step, from the download to the setup!

Thanks,

---

### Post by JohnElway on 2010-08-20
Are you having any problems other than not being able to shutdown from the UI? There's a well-known combo of problems that affect new 10.04 installations: can't shutdown or restart, no sound, can't mount USB drives. I encountered these problems but easily fixed them all by installing the policykit package with this command:

```
sudo apt-get install policykit policykit-gnome policykit-desktop-privileges
```

Then I rebooted the computer:

```
sudo reboot
```

---

### Post by kuramayoko10 on 2010-08-20
Thanks for the reply,

I got it fixed now... now I could include to the panel the "advisors" and some applets already!
I will just have to find the messenger application and dropbox and it will be as it was before!

And for now the problem with the "power off/reboot" and mounting devices is fixed.

The only thing that I would like to know is... what is this tpackage that I installed...?  it reseted my grub list to only one linux version!
I wanted to that too actually!

Thanks

---

