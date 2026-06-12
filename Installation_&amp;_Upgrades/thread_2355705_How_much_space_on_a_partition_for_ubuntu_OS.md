---
title: "How much space on a partition for ubuntu OS?"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by david503 on 2017-03-15
So I'm installing ubuntu for the first time- I want to know what's a good partition size for the OS?  (as distinguished from my files and applications),

I know the minimal requirements, but what I want to know is what's a "good" size.  

So, for example- I have a terabyte drive, I'm thinking I give the OS partition 100gb, and then periodically make disk images of that parition so that I can more easily restore if the drive fails.  The other partition for my data will be the 900gb.   (my data is being backed up to the cloud separately so I'm not worried about that.)

Does that sound like a good plan/size?

Also- I'll have a virtual running windows- do I need a seperate partition for it as well, or can it just live as a (large) file within the data partition?  (I guess that's a separate issue sorry)

thanks guys

---

### Post by oldos2er on 2017-03-15
I usually have a root partition size between 20 and 25GB, which seems to be more than enough.

---

### Post by grahammechanical on 2017-03-15
It will also depend on how many additional programs/applications you intend to install and what type of application they are. I may be wrong but I think that the VM and the OS in it will be on the same partition as Ubuntu. So, you will need to allow space for that. My machine is under powered for a VM and I do not have a copy of Windows so I cannot advise as to the size of that combination.

Regards

---

### Post by Impavidus on 2017-03-16
Normal would be about 20GB. I use 30GB. My hard drive is larger than I need, so better err on the safe side. That is for the OS including all applications, but not my documents. In Linux, there's not such a clear division between the OS and the applications. Many parts, like the GUI, which are part of the OS in Windows are just another application in Linux.

I've no experience with virtual machines.

---

### Post by Tadaen_Sylvermane on 2017-03-16
I do root of 15gb, never have broken half that. I keep data on it's own partition symlinked into my /home/$USER. Works fine for me.

---

### Post by RobGoss on 2017-03-16
If you are serious about using Ubuntu and it will be one of your primary desktops them you want to assign enough space. I think a **100-GB **is a good size for the Ubuntu partition. Some people only give **20 to 30 GB** because they like testing different OS's, I my self have about** 8 machines **and only one is a dual boot system with Kubuntu and Mint, the rest of my machine each has a different version of Ubuntu and other Linux distributions

---

