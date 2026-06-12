---
title: "Install 20.04 on existing 18.04 LTS alongside Win10"
date: 2020-06-12
forum: Installation &amp; Upgrades
---

### Post by Frantic_Earthling on 2020-06-12
Rather than upgrading from 18.04 LTS to 20.04 LTS, I am thinking of doing a fresh install of 20.04

I currently have 18.04 LTS installed alongside Win10.

My question is: can I just launch the 20.04 install and will it offer to install in the same partition as 18.04, over 18.04 and erase it? 

I do not need to keep any old data nor my previous 18.04 configuration  and I understand they will be lost.

Will it find Win10 and leave it intact in its partition?

I know that before the 20.04 install actually starts doing something irreversible, I am offered the choice of "erasing Ubuntu 18.04 LTS and install 20.04" but does this leave my Win10 partition intact and will GRUB include Win10 it as it does today?

---

### Post by ActionParsnip on 2020-06-12
Yes the install CD will see the current install and offer an upgrade. I suggest you perform a full backup before you do this to safe guard your data (Unless there is nothing of value to you, in which case barrel on through).

---

### Post by Frantic_Earthling on 2020-06-12
> **ActionParsnip said:**
> Yes the install CD will see the current install and offer an upgrade. I suggest you perform a full backup before you do this to safe guard your data (Unless there is nothing of value to you, in which case barrel on through).

Thanks for your answer :), but I do not want to upgrade. I want to make a fresh install and just keep Win10 as is.

---

### Post by tea for one on 2020-06-12
In the installation process, when you reach the page **Installation Type**, choose "Something Else".

Then you have the choice to use (and format) your existing Ubuntu partition(s).

Do you already have an **EFI** partition?

---

### Post by Frantic_Earthling on 2020-06-12
> **tea for one said:**
> 

...

Do you already have an **EFI** partition?

Yes, I do.

---

### Post by tea for one on 2020-06-12
Therefore, you can select "Something else" during the installation and choose your partition(s).

Ubiquity will automatically find the EFI partition - user intervention not required.

Grub should also pick up your Windows 10 (assuming you have shut it down cleanly) i.e. not invoking Quick boot, fast start-up or similar phrases.

By the way, you have backed up your Windows data?

---

### Post by Frantic_Earthling on 2020-06-12
Well, I just did it.
Fresh install of 20.04 over my old 18.04 LTS that was dual booting with Win10.
20.04 erased my old version and left Win10 as it was.
Could not be simpler!
My dual boot still works perfectly.
Many thanks to the people at Canonical!

---

### Post by Frantic_Earthling on 2020-06-12
> **tea for one said:**
> 

...

By the way, you have backed up your Windows data?

Guess what?
Yes I did!
Thanks for your help Tea for One :)

---

### Post by tea for one on 2020-06-12
Splendid - Please mark the thread as solved - it is helpful to other users.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

