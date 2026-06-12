---
title: "Ubuntu 11.10 Desktop Environment Freezing"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by jboniello on 2012-01-26
Hello everyone,  I am extremely frustrated and desperate for help. Let me say that I consider myself a bit of a n00b BUT I do know at least the basics, I can use the terminal well enough to do basic things, so I am not completely lost, but I am still lost on some things. 
 I am dual booting windows and ubuntu on a lenovo pc I bought a couple of weeks ago.  I, for some reason, was avoiding ubuntu, but when I could not get any other distro to work on this computer I decided to try 10.10.  It worked and I had a functioning buntu desktop.  It asked me to upgrade to 11.04, I held my breath and pressed ok. It still worked! It had been working for some a week or so when it asked me to upgrade to 11.10.  I did.  Now when I boot it asks me to login, I do and the screen freezes.  I can access the computer via ssh and issue commands.  I updated the /etc/default/grub file to insert nomodeset and noacpi and noapic to test if those would work (in different combinations), they did not.  I have searched forums upon forums and google for hours, nothing so far has worked.  :confused:  

Last night I tried to reinstall 10.10 and it worked.  I have a feeling that it is something with the newer kernel that is not playing well with my system, but I am not sure how to check this. I also tried a fresh install of 11.10 from a live cd, it gave me a grey screen, the same thing mint 12 was giving me (the reason I gave up on that!) I have an ati graphics card, and had fglrx installed on 11.04.  When I upgraded I thoguht maybe the driver was broken in some way.  I followed instructions to purge and reinstall fglrx driver, did so via ssh.  This worked for 30 seconds before the system froze.  I am tired and frustrated and wishing I did not have to go through all of this to get a linux distro up and running.  I cannot imagine the rest of the world, who aren't even willing to learn how to do basic functions, getting one of these up and running with success.  PLEASE help!!!](*,):mad:

---

### Post by Gstrazds on 2012-01-26
Hi there .. I can't speak directly to your notebook issue; I can however offer comments..

You need offer up, the make - model, video card, hardware specs; although I would suspect Video.. 

[https://answers](https://answers).**launchpad**.net/**ubuntu**/+[B]questions

[/B]to see if your problem is there.. If not; you would need to go through the process to create a problem report... 

I have an nvidia card; It also has problems.. to many open windows = blank windows

The original reason for responding to your assistance request.. Last couple of days I noticed my screen "Desktop environment" freezing up on me... "connected" that the optical mouse of mine is finally failing; removing and re-inserting the usb connector caused the system to come alive again.. 

So the possibility exsists that your mouse is guilty, although unlikely; from what you've said

Glenn

---

### Post by jboniello on 2012-01-26
Sorry, forgot to include the specs, I was up really late and woke up too early!

Desktop PC, Not notebook.

Ideacentre K330 Desktop Computer; 
Intel® Core i3-2100; 
4GB DDR3-1333 RAM; 
1TB 7,200RPM Hard Drive; 
DVD±RW Drive; 
912-V253-007 AMD Radeon HD 6670 1024MB GDDR5 PCIe 2.0 x16 Video Card

Those are the basics.  Hopefully this will help people.  I could go into windows and get more info if needed.  

Like I said, I am very frustrated and have been researching possibilities.  Thanks 

Also, not sure how to create a problem report?

---

### Post by jboniello on 2012-01-27
Anyone?

---

### Post by jboniello on 2012-01-27
The 2D version works.  3D is still stuck.

---

### Post by Gstrazds on 2012-01-28
Hi there Did you look for your ati proprietary driver in the System/Additional drivers tab...

I guess you must have since you got 2D working.. I don't know what your seeing; compiz 
enables 3D effect that may not be enabled

The process for creating a problem report is self explanatory.. also do most of the work for you.. just have to fill in the form..

---

### Post by jboniello on 2012-01-29
Yup, proprietary driver is enabled, also tried without but that did not work.  I've been running 2D fine for the last fw days now, may just stick with that.  It is annoying though to not be able to use the OS as it is intended.

---

