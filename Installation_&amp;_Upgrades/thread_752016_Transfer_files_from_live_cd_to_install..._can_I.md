---
title: "Transfer files from live cd to install... can I?"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by sigment on 2008-04-11
Hello all! First post w00t!

Well, I have a question, I have searched and searched with no avail...

I have the latest version of Ubuntu installed on my toshiba portege r200 with 100% functionality after a few hours on config... but

My previous installation of nUbuntu (the network version) was horrible, no wireless, not ethernet, no bluetooth, only usb cdrom support (thank goodness as I don't have an onboard cdrom).  there is no support or even active developement as far as I can tell...

The Question: Is there any way possible for me to boot to the live nUbuntu cd and transfer the programs suite of network tools to my Ubuntu installation easily?

 They appear to all be in one folder on the live cd... can I just copy them or will they need to be recompiled? I am not sure... I only use CentOS for webserver usage, and never a desktop replacement...

I have tried with NO success to compile a few of the tools. I have tried absolutly every avenue I have found or imagined to install these tools...

any links, suggestions or thoughts are appreciated... and No, I dont need to be spoon fed an answer but any help would be great.

Thanks, and I am glad to be part of the forums...

---

### Post by kellemes on 2008-04-11
I wonder what network tools you mean..
Since I can't imagine there isn't any way of getting the needed tools on Ubuntu through repo's.

---

### Post by sigment on 2008-04-11
> **kellemes said:**
> I wonder what network tools you mean..
Since I can't imagine there isn't any way of getting the needed tools on Ubuntu through repo's.

They are network pentesting tools, I am particularly interested in the ones pertaining to web and network security as I am running a commercial webserver... The rest I am not really interested in, except maybe the bluetooth tools to play with my new phone... I only seem to find 1 or 2 in the public repositories...

---

### Post by Gen2ly on 2008-04-11
I'll say it, I'm confused.  nUbuntu can't install over the network, I'm guessing.  if this is the case, why not use the regualr ubuntu CD?  Yeah files could be transfered but some things like /etc/fstab will have specific information for using only a CD.  I'd really wouldn't recommend this.  There's a lot of Linux distro's out there maybe there is another that has an easy network install.

---

### Post by sigment on 2008-04-11
> **Dirk.R.Gently said:**
> I'll say it, I'm confused.  nUbuntu can't install over the network, I'm guessing.  if this is the case, why not use the regualr ubuntu CD?  Yeah files could be transfered but some things like /etc/fstab will have specific information for using only a CD.  I'd really wouldn't recommend this.  There's a lot of Linux distro's out there maybe there is another that has an easy network install.

Ok, to clarify... 

I am asking if I can copy the files from the nUbuntu Live environment onto my hdd where regular ubuntu is installed already. and IF yes, What folders should I pay attention to? The live environment looks just like an installed environment, just it is loaded in ram not on the hdd. 

 Not a network install, although I did install through my PXE install server:p.

---

### Post by Gen2ly on 2008-04-11
Pardon my bafoonishness.  Butwhy would you want to dothis?

---

### Post by sigment on 2008-04-11
OK, Thanks for everything, by only questioning my intentions in this matter, you have solved the problem.

























not. 

how can I unregister for these forums? 

~unsatisfied customer, 
sigment

---

### Post by Gen2ly on 2008-04-11
Ok, I'll explain a bit.  Transfering files from an existing from on OS to another is likely to have problems.  Most importantly is version mismatches which don't always work with their respective libraries.  This could cause problems in security, and could cause the system to be unstable.  We Ubuntu users are attached to our machines and would probably cower at such an undertaking, we don't like to see that happen. :)

---

### Post by wannadumpwindows on 2008-04-11
You could search the repos, and see if the tools you're looking for are available. There's a bunch in there. All kinds of good stuff. If you're looking for a specific tool, try google if it's not in the repos.

---

### Post by twist2b on 2008-04-11
installing more data from the cd can be easy through sanaptic package manager
under "system>administration"
when it opens select settings>repositories
select the CD at the bottem for "installable by CD-ROM"
stop being a baby thinking the world revolves around YOU. It does not. Ubuntu was made for the people who were not jerks. So you can go back to Windows, and stay there for all we care,

Installing packages from the server online is both safe and your best bet for extra data/applications

---

### Post by sigment on 2008-04-12
> **twist2b said:**
> installing more data from the cd can be easy through sanaptic package manager
under "system>administration"
when it opens select settings>repositories
select the CD at the bottem for "installable by CD-ROM"
stop being a baby thinking the world revolves around YOU. It does not. Ubuntu was made for the people who were not jerks. So you can go back to Windows, and stay there for all we care,

Installing packages from the server online is both safe and your best bet for extra data/applications

Thank  you very much for your insight, I will try the cdrom method through synaptic. 

As for being a jerk, I  thought public forums were for passing knowledge and communication. I have read these forums for quite sometime, and very often I see "baffoons" offer no info while questioning motives etc.  

Again, thanks for the tip:)

---

