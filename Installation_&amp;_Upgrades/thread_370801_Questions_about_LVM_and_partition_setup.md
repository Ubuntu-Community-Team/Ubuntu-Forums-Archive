---
title: "Questions about LVM and partition setup"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by Corvo78 on 2007-02-26
I'm planning on using LVM during my install. Allthough I still have a few questions:[list=1]
[*]Can Windows access a Logical volume (LV) of a Linux LVM?
[*]Is there a GUI to manage a Logical volume group (LVG)?
[*]If for some reason Ubuntu b0rks (unlikely, I know), does a new install recognize the allready existing Logical volume group?
[*]If a second drive is added to the group, isn't this form of striping unsafe because "if 1 fails, all fail"?[/list]



Currently I'm thinking of this partitioning scheme...
[list][*]250GB (hardware) Raid0 mirror:[list]
	[*]100MB EXT3 for **/boot**
	[*]249,9GB reserved for LVM:[list]
		[*]10GB EXT3 for **/** (root)
		[*]2GB ReiserFS for **/var**
		[*]~220 EXT3 for **/home**
		[*]13GB unallocated, *for possible Logical volume (LV) growth*.[/list][/list]
[*]200GB:[list]
	[*]2GB for **Swap**
	[*]198GB EXT3 for **/home/username/downloads**[/list]
[*]500GB:[list]
	[*]500GB EXT3 for **/home/username/videos**[/list][/list]


Some remaining questions:[list=a]
[*]Is it a good idea to reserve some unallocated space for growth of the LVG?
[*]Would it be a better idea for swap to reside on the Raid0 drive?
[*]Is ReiserFS a good idea for /var (which is used for logging I believe)?[/list]

---

### Post by louis_nichols on 2007-02-26
> **Corvo78 said:**
> I'm planning on using LVM during my install. Allthough I still have a few questions:
Can Windows access a Logical volume (LV) of a Linux LVM?

As of now, there is no windows driver for LVM.
> **Corvo78 said:**
> 
Is there a GUI to manage a Logical volume group (LVG)?
I dunno. It would be helpful to find out about one, though. But LVM is not that difficult to use from command line
> **Corvo78 said:**
> 
If for some reason Ubuntu b0rks (unlikely, I know), does a new install recognize the allready existing Logical volume group?
Yes. I have in fact reinstalled (K)Ubuntu about 4 times on the same LVM setup. I use the alternate CD for this. I'm not really sure about the capabilities of the LiveCD installer when it comes to LVM.
> **Corvo78 said:**
> 
If a second drive is added to the group, isn't this form of striping unsafe because "if 1 fails, all fail"?
I guess that's true. I have only one HD, so I guess that's not an issue for me. Anyway, even if you do use a volume group for each HD, if the one containing the setup for the entire LVM fails, I don't think you'll be able to recover the data from the others. I think a mirroring raid would be the way to solve this.

> **Corvo78 said:**
> 
Currently I'm thinking of this partitioning scheme...
[list][*]250GB (hardware) Raid0 mirror:[list]
	[*]100MB EXT3 for **/boot**
	[*]249,9GB reserved for LVM:[list]
		[*]10GB EXT3 for **/** (root)
		[*]2GB ReiserFS for **/var**
		[*]~220 EXT3 for **/home**
		[*]13GB unallocated, *for possible Logical volume (LV) growth*.[/list][/list]
[*]200GB:[list]
	[*]2GB for **Swap**
	[*]198GB EXT3 for **/home/username/downloads**[/list]
[*]500GB:[list]
	[*]500GB EXT3 for **/home/username/videos**[/list][/list]
The setup looks OK. Although, because of the advantages of LVM, I wouldn't directly allocate ALL that space. I only enlarge logical volumes as needed by 1 to 10 GB once as needed. Also, I recommend using reiserfs on LVM, because it allows resizing without un(re)mounting, whereas for ext3 you have to un(re)mount. See [here]("http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html")

> **Corvo78 said:**
> 
Some remaining questions:[list=a]
[*]Is it a good idea to reserve some unallocated space for growth of the LVG?
[*]Would it be a better idea for swap to reside on the Raid0 drive?
[*]Is ReiserFS a good idea for /var (which is used for logging I believe)?[/list] These are all answered above., except b, which I don't really know.

---

### Post by primski on 2007-02-26
> **Corvo78 said:**
> 
[*]Is there a GUI to manage a Logical volume group (LVG)?

There is evms with evms-ncurses.

---

### Post by louis_nichols on 2007-02-27
Well, what do you know? It IS possible to read LVM2 from windows.

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

EDIT: And also, there is a pretty nice GUI. See here: [http://evms.sourceforge.net/gui_screen/](http://evms.sourceforge.net/gui_screen/)

---

### Post by Corvo78 on 2007-02-27
Thank you, that's good info!

:popcorn:

---

