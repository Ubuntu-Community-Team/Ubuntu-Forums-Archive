---
title: "How much drive space for Kubuntu OS?"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-05-13
I'm new to this Linux endeavor, even though I've installed Fedora, FreeBSD and Kubuntu in old PCs just to see the looks and all that.
I'm highly considering adding a 2nd HDD to home PC to install Kubuntu.
My PC has XP Pro on a SATA drive and I don't want to touch this for now.

So, I will add the 2nd drive but wondering what's the best approach in terms of sizing the main Kubuntu OS patition.
When I install XP on any PC I usually leave or create a 10~20 GB partition for the OS and leave the rest as a 2nd partition for data storage, etc.....so I try not to install anything on the main OS partition.

Do Linux users always leave OS partition alone just for the OS?
What would be a "normal" or decent partition size for the OS?

The 2nd drive I will use for Kubuntu I think is about 40 or 50 GB.

Thank you guys,

---

### Post by geek2330 on 2007-05-13
BTW - the new drive will be an old IDE drive.

---

### Post by louieb on 2007-05-13
Unlike streaming music this is something I know about. 
For the /  (root) partition 5 - 10 gig is plenty. 
and for a swap partition 1 to 2 times memory size. 
How you use the balance is up to you. I normally put my /home directory on a separate partition, and allocate the balance of space to it.  
For a visual check out the partitioning page at [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") or another good on is the [Dual Boot site]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning")  and last and least is my  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")   general notes on partitions.

---

