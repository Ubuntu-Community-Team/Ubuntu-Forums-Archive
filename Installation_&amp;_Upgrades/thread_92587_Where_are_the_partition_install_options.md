---
title: "Where are the partition install options?"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by AgentZ86 on 2005-11-19
Hi all this is my first post

Just downloaded the latest install version x86 platform.

I could not install because I did not see an option for selecting which partition I desire to install to.

I see many selections to re-write and format partitions etc. but no option that I could see anyhow regarding making a selection of which partition I desire to install to.

Anyhow else familiar with this topic.

I have an 80 gig HD with hda1-ntfs, hda2-ext,hda3-linux swap,hda4 extended, hda5,hda6,hda7 logical partitions in the extended partition.

I want to install to hda6 logical partition in the extended partition.

All other distros appear to give me options for choosing which partition to install to:

How do you select which partition to install ubuntu

Please advise

---

### Post by aysiu on 2005-11-19
You don't see something like [manually edit the partition table](http://users.bigpond.net.au/hermanzone/p2/i0916op.gif)?

---

### Post by AgentZ86 on 2005-11-20
Thanks for the response,

Yes I did see something about this but I do not want to edit the partitions I want them to stay the same I've already created my partition with Qparted and I just need to set the mounting points etc. and install Ubutu, but I don't want to change any of the other partitions I'm concerned of overwriting my main partition spaces.

I want to install to hda7 with mounting point / should be fine, but there did not appear to be a custom install options to allow my to choose or at least I did not understand it perfectly.

I kept getting the menu screen and then well I'll retry and post my actuall screen info there.

But in general if you know please describe the process of installing and selecting a partition.

But not making changes to the existings partitions only the one I'm installing to.

Please advise
thanks

---

### Post by aysiu on 2005-11-20
Manually editing the partition **table** does not mean editing the partition sizes and number. It means you get to pick which partitions you want mounted where. If I ever want to install over a partition with Ubuntu, I always pick this option.

---

### Post by AgentZ86 on 2005-11-24
I've already partitions the drive the way I want and have serveral OS's already on the Primary partitions, and extended logical partitions.

Having said that I'm having trouble continuing with the install cause I do not understand the menu screens.

The main thing is that I do not want to overwrite and partitions only perhaps format and install ubuntu to a partition I would like to choose.

I did not see an such selections for this.

Please advise with step by step install instructions and selections during the process in order to install ubuntu on hda7

I have currently hda1-ntfs, hda2-ext.3,hda3-swap,hda4 extended,hda5-logical,hda6-logical,hda7-logical

Please advise
thanks

---

### Post by aysiu on 2005-11-24
[QUOTE=AgentZ86]
Having said that I'm having trouble continuing with the install cause I do not understand the menu screens.

The main thing is that I do not want to overwrite and partitions only perhaps format and install ubuntu to a partition I would like to choose.

I did not see an such selections for this.[/QUOTE] There should be an option--underneath all the ones that say "erase" something or other--called "Manually Edit the Partition Tables." That's the one you want.

See the attached screenshot for more details (it's the fourth option).

For more information, check out Herman's [guide to dual booting](http://users.bigpond.net.au/hermanzone/). It may not be your exact situation, as it assumes you have one big Windows partition that needs to be resized, but a lot of the same principles apply (select partitions and mounting them in particular ways).

---

### Post by AgentZ86 on 2005-11-24
Thanks and I've actually took a chance with the manually option.

I must say it was not easily understood, they need to change this to express to people that they will not be writing anything to the drive.

Also it will not go foward unless you select your partition and actually make it a root, and what type of format.

I see now that all the features are there but difficult to navigate and makes one scared to go any further.

The bottom line answer I found out for this is:
Select manually option
Then when the screen comes up you highlight or use the arrow keys to navagate down to your desired partitions in which you wish to install Ubuntu.
Then when that screen comes up you will see some options for that partition and you must select an options that is different then what is listed for example if you have set up your drive using qparted at first, and then try to install ubuntu, then you have a partition but it's not formated for any OS
So at this point you should highlight the option for the drive format, and select ext.3
Then highlight the mounting point as / for root partition.
Then down to the bottom to finish or done and it will start to install.

Not very simple to understand that you must make a selection and also prior to this there should be some type of direction to those who already have partitions that they would like to use.
They need to make this simpler with an option to use a partition you already have, then select which format from a list, then next screen should be which mounting point etc. on seperate screens I would think could be a little simpler to understand

Thats just my opinion, but now that I know this I could easily do it again.

I have the similar problem with CentOS I'm afraid to go further, but want to install it.
 
Anyhow thanks for the help

---

