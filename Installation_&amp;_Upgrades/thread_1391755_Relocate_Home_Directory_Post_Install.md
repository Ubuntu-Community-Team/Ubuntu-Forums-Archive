---
title: "Relocate Home Directory Post Install"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by santhony on 2010-01-27
I'm trying to relocate my home directory which currently resides at the default, root location /home/user.

My Systems Specs:
Karmic64
Root resides on a Raid0 LVM MD0
NEW Drive resides on Raid0 LVM MD1

I installed a new disk on a LVM(Logical Volume Manager), and now want to move my default home directory to the new location.

I did rsync my home directory from the OLD to the NEW.
When I do update my /etc/fstab with the NEW home location, I recieve errors upon rebooting, that certainly relate to permission issues, including some from Nautilus that mentions permissions issues...

I also tried to update the USERS/GROUP Manager with the NEW location but after reopening the USERS/GROUP manager, I can see the original location has been reverted back.

I can create a new user and succesfully map their home directory to the NEW home location on my MD1 LVM.

Anyone have any ideas or links on home to remap their existing HOME directory to a new location?

Thanks

---

### Post by rhills on 2010-01-27
Hi,

I'm a newbie to Ubuntu, but I thought this would be a relatively common question, so I Googled "linux howto relocate home" and came up with quite a useful-looking list of results.

The following looked pretty comprehensive step-by-step instructions to me:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This one was a bit more terse, but also looked useful:

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

I note that I've not yet tried either of these, but I probably will in the near future.

HTH,

Rob Hills
Waikiki, Western Australia

---

### Post by santhony on 2010-01-30
Thanks.. I'll look them up and give it a try...

---

