---
title: "Re-installing the system"
date: 2008-05-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-05-14
I have a doubt I hope you can help me with:

If I have a working installation of Ubuntu in a partition, then for whatever reason I choose to re-install but do NOT check the "format" checkbox... what will happen?

Do all my installed programs stay? my /home? Is that a smart thing to do?

---

### Post by hermes0710 on 2008-05-14
I think you won't be able to proceed. What you are asking is usually a suggestion on how to reinstall grub (because the installation proceeds normally, it installs grub but fails to install any other packages). Anyway, why do you want to proceed this way? I am not fond of overwriting things

---

### Post by Gina on 2008-05-14
I know the installer issues a warning in this case - that problems may arise from a mixture of different dated software.  Not good practice and I too would NOT recommend it.  It's better to use a separate /home partition to retain your documents and settings.

Why do you want to reinstall if you have a working system?

---

### Post by Bou on 2008-05-14
> **hermes0710 said:**
> Anyway, why do you want to proceed this way? I am not fond of overwriting things

Because of [this]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-May/thread.html") (see the "separate /home" part)

Basically, I proposed a system to install /home on a separate partition and the devs told me that there's no need for that, because ubuntu now recognises and preserves existing /home folders.

The thing is, I tried that yesterday and it didn't work, obviously because I was choosing to format the partition. So I wonder if NOT formatting it is a sensible option when re-installing.

---

### Post by plun on 2008-05-14
> **Bou said:**
> Because of [this]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-May/thread.html") (see the "separate /home" part)

The thing is, I tried that yesterday and it didn't work, obviously because I was choosing to format the partition. So I wonder if NOT formatting it is a sensible option when re-installing.

I don't get it how a format tool can preserve specific folders...:confused:

All tools which I knows are really primitive and just wipes a specific partition.

It must be different tools included which first moves folders/files
,then format and at last moves ./home back on the partition.  

Maybe we needs a blueprint....:)

---

### Post by Bou on 2008-05-14
> **plun said:**
> I don't get it how a format tool can preserve specific folders...:confused:

Precisely. I was formatting the partition, so /home was erased.

So I take it the only option to preserve /home is NOT to format, but as hermes says, how good can that be?

EDIT: [here]("https://wiki.ubuntu.com/UbiquityPreserveHome") you can read what exactly happens when you install over an existing partition. Any thoughts?

---

### Post by ronacc on 2008-05-14
I have always found ubuntu's partioner a pain in the a** to convince to do things the way you want it to, if you want it to do anything other than accept the default . In the discussion you referenced there seems to be some confusion between folder and partition , I don't believe there is any way to preserve a folder UNLESS that folder is on it's own partition . Trying to format only parts of a partition would be a real disaster if it was even possible . The safest way to handle it is to keep data you want to persist on a seperate drive and pray that the installer dosent do something stupid like formating every drive in the box.

---

### Post by rossmoore on 2008-05-14
I have successfully done this. When I first installed Ubuntu, I asked the Ubuntu Live CD installer to create me a 20Gb partition, formatted to ext3 for the / filesystem. Then 4Gb for swap, and 250Gb or so to be formatted as ext3 and mounted as /home.

I then had problems with Ubuntu and thought I'd try Kubuntu (I'm considering going back - I'm not sure if my problems in Kubuntu are better or worse than the ones I had in Ubuntu). So I asked the Kubuntu Live CD installer to leave the 250Gb ext3 partition alone (not to format it), but to mount it as /home, and to format the 20Gb partition that had Ubuntu on it and mount that as /.

It has worked perfectly - I removed (backed up) most of the hidden files and folders to prevent them confusing Kubuntu at least until I wanted to try transferring those settings.

---

### Post by plun on 2008-05-14
> **Bou said:**
> 
EDIT: [here]("https://wiki.ubuntu.com/UbiquityPreserveHome") you can read what exactly happens when you install over an existing partition. Any thoughts?

OK, thanks for the blueprint...

> **Design**

We will add functionality to partman and ubiquity that checks to see if the requested root partition is not empty and contains a /home directory. If this is the case, debconf will present the user with a question similiar to the following:

This filesystem already seems to have some content on it.  **Do you want to preserve this data and remove the following:**
...list of directories and top-level files to be removed...

This question will be preseedable, so that OEMs can blindly say yes to it. 


Tested/Untested, who tested...:confused:

Finished, quality :confused:

Delievered :confused:


[https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-preserve-home](https://blueprints.launchpad.net/ubuntu/+spec/ubiquity-preserve-home)

Implementation:  Beta Available 

Definition: Pending Approval (Needs guidance)

---

### Post by ronacc on 2008-05-14
my thoughts on the second item you referenced are that it looks like a recipe for disaster , removing all those folders and not formating the partition invites a real screwup.At the very least it might result in a degree of fragmentation that would leave Windows green with envy.

---

### Post by cariboo on 2008-05-14
I think PCLinuxOS gives you the choice if you already have a distribution installed, to leave /home as it is and just install on the rest of the disk. This is assuming that you have already partitioned your hard drive and don't want to change the file system to something else. I would like to see Ubuntu do something like this.

Jim

---

