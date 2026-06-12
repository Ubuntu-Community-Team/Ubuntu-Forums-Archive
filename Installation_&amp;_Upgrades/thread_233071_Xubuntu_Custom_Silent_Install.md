---
title: "Xubuntu Custom Silent Install"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by Jeffrey903 on 2006-08-09
Hello,

I currently work at a charity called PC Renew.  We take old donated computers (usually about 350 - 600 MHz, 64MB - 128MB RAM, 4 - 10GB harddrives, etc), nuke the harddrives, replace any bad parts, and then install Windows 98 or 2000 on them (we have a deal with Microsoft to do this legally because we are a charity).  We then donate the PCs to people who can not afford to buy new ones.

We are currently looking at installing Linux on them instead of Windows.  I currently am trying out the Xubuntu Alternate CD on a refurbished computer.  The problem is that it takes a long time to install the OS, download and install the updates, install some other programs, and customize the system.

I believe that I finally have gotten my one test system to how we want it, and I was wondering if there was anything I could do to automate the entire process for future computers?  I was hoping that I could make a CD (or DVD if I have to) where basically I could pop it to the computer, and with minimal interaction from a human it would install it to how I wanted.

Is this possible, and if so, how would I go about doing it?  I do not know much about the Linux command line.

Thanks for your help in advance.

---

### Post by randell6564 on 2006-08-09
> **Jeffrey903 said:**
> Hello,

I currently work at a charity called PC Renew.  We take old donated computers (usually about 350 - 600 MHz, 64MB - 128MB RAM, 4 - 10GB harddrives, etc), nuke the harddrives, replace any bad parts, and then install Windows 98 or 2000 on them (we have a deal with Microsoft to do this legally because we are a charity).  We then donate the PCs to people who can not afford to buy new ones.

We are currently looking at installing Linux on them instead of Windows.  I currently am trying out the Xubuntu Alternate CD on a refurbished computer.  The problem is that it takes a long time to install the OS, download and install the updates, install some other programs, and customize the system.

I believe that I finally have gotten my one test system to how we want it, and I was wondering if there was anything I could do to automate the entire process for future computers?  I was hoping that I could make a CD (or DVD if I have to) where basically I could pop it to the computer, and with minimal interaction from a human it would install it to how I wanted.

Is this possible, and if so, how would I go about doing it?  I do not know much about the Linux command line.

Thanks for your help in advance.

First, let me say COOL!  I Love you guy's!

Xubuntu is a compact OS. Dont know why it would take "a long time" to install!  AND, what "other programs" are you refering to?  Why do you want to customize it if you are donating the box to the less fortunate?

"I was hoping that I could make a CD (or DVD if I have to) where basically I could pop it to the computer, and with minimal interaction from a human it would install it to how I wanted."

In other words, you want it to automatically configure itself to the custom settings that you chose.  I'm not sure thats possible, unless you are among the xubuntu staff that created the OS.  Neat idea though!

The problem that I see here is that, everyone that receives one of these donated PC's is not going to want the same thing.  Why not just install the system, enable all the repositories and let the owner decide?  

There are literally a Gazillion applications available to Linux users!

---

### Post by Jeffrey903 on 2006-08-09
It took about an hour and a half to install the Xubuntu Alternate on my test machine.  I figured it would be a lot faster, but it wasn't.

I haven't added any unusual programs.  I added stuff like flash player, java, some media codecs, etc.  I also added a few basic games so people can play them.

Is it possible for me to create a disk image and then use that to install it on the other computers?

---

### Post by randell6564 on 2006-08-09
> **Jeffrey903 said:**
> 
Is it possible for me to create a disk image and then use that to install it on the other computers?

That would involve much more than I am qualified to give, my friend!

Check out the desktop support forum.  I have never heard anything mentioned in these forums that would suggest that you can.

An "hour and a half"?!  Somthing is wrong with that picture! I use ubuntu, (fatter than xubuntu), and it installs in 20 minutes max!

---

### Post by Jeffrey903 on 2006-08-09
Keep in mind that this computer is a 350MHz with 128MB of RAM and a 6.5GB harddrive.  I can also install Ubuntu (or Xubuntu) on my computer in a fraction of the time.

Hopefully someone else has an answer, as it would really help me out.

---

### Post by randell6564 on 2006-08-09
> **Jeffrey903 said:**
> Keep in mind that this computer is a 350MHz with 128MB of RAM and a 6.5GB harddrive.  I can also install Ubuntu (or Xubuntu) on my computer in a fraction of the time.

Hopefully someone else has an answer, as it would really help me out.

Forgive me, but your OP say's that it takes you an hour and a half to install xubuntu. Which is it?

---

### Post by Jeffrey903 on 2006-08-09
Sorry, I guess I wasn't being clear.  It took about an hour and a half to install Xubuntu on the 350MHz machine which will go to charity.  It took me a fraction of the time to install it on my AMD 3500+ home personal machine (I installed it there first just to learn a little about Xubuntu).

---

### Post by randell6564 on 2006-08-09
> **Jeffrey903 said:**
> Sorry, I guess I wasn't being clear.  It took about an hour and a half to install Xubuntu on the 350MHz machine which will go to charity.  It took me a fraction of the time to install it on my AMD 3500+ home personal machine (I installed it there first just to learn a little about Xubuntu).

That makes sense!  I'm sorry, I'm just wasting your time! Again, I suggest posting in the Desktop support forum. Look for 'aysiu' or 'landefor'.  They are very knowledgable!

---

### Post by avtolle on 2006-08-09
Good for you! Obviously, the donees are likely not to have broadband or, in some cases, dial up net access, making your quest even more important, IMHO. I agree with randell6564's suggestion to look at the Desktop forum, and there will (I hope) be someone there who will be able to guide you.

---

### Post by picpak on 2006-08-09
There are programs that can do this:

[http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/](http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/)

---

### Post by orb9220 on 2006-08-09
I think what your concerns are most likely the Updates? After the install.

If this is correct I have also asked about ubuntu updating thier ISO's so that triple figure like (130-150 packages required for updades) would not be required.

But thier answer was a resounding No they had no intention in doing so.

I would Love an ISO that was update with all packages and easy ebuntu for codecs,java,etc to automatically be installed. 

Would cut HOURS! out of the install time. Now you may say it dosn't take hours. No the process itself of updates and easy ubuntu actually doubled the base install time. 

But then I had to spend time searching for why the codecs were missing in the first place and how to get them and java installed.

And then thier is the configuring the xorg.conf file for video
And then if there is wireless or network to configure.

Yes now I can do a complete configured system with full support in 90 mins.

But the first time was a bear.

And also where you are going to have a bit of trouble is for each system that is different you will probally have to config  a few things manually like video,wireless,sound not so much. But you may want to keep track of changes for the different configs so you don't have to redo them from scratch.

Good Luck!

---

### Post by randell6564 on 2006-08-10
> **orb9220 said:**
> 
And also where you are going to have a bit of trouble is for each system that is different you will probally have to config  a few things manually like video,wireless,sound not so much. But you may want to keep track of changes for the different configs so you don't have to redo them from scratch.

Good Luck!

Thats Why I suggested that you just install and update.

---

### Post by Jeffrey903 on 2006-08-10
I think a lot of my problems will be solved now that 6.06.1 has been released.  I won't have all of those updates to install anymore.

---

