---
title: "Any considerations needed for installing on laptops with hybrid drives?"
date: 2016-07-23
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2016-07-23
Hi,

I was considering getting a new laptop (like [https://www.amazon.com/Dell-Inspiron-i7-6700HQ-Processor-Keyboard/dp/B01G07JUEI/ref=sr_1_4?s=pc&ie=UTF8&qid=1469277912&sr=1-4&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011&tag=gdext-20](https://www.amazon.com/Dell-Inspiron-i7-6700HQ-Processor-Keyboard/dp/B01G07JUEI/ref=sr_1_4?s=pc&ie=UTF8&qid=1469277912&sr=1-4&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011&tag=gdext-20) or [https://www.amazon.com/Dell-Inspiron-i7559-2512BLK-Generation-GeForce/dp/B015PYZ0J6/ref=sr_1_1?s=pc&ie=UTF8&qid=1469277912&sr=1-1&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011](https://www.amazon.com/Dell-Inspiron-i7559-2512BLK-Generation-GeForce/dp/B015PYZ0J6/ref=sr_1_1?s=pc&ie=UTF8&qid=1469277912&sr=1-1&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011)) to install Ubuntu alongside Windows 10 or dual boot, and got to read a little about hybrid drives. 

My questions are: 

[LIST]
[*]Does the presence of SSD require me to handle it differently, or can I go ahead and install it for dual boot like other laptops with regular hdd?
[*]Is there anything I should know about SSD and Linux? Or SSD?
[*]Also, which is better, 8 GB or 128 GB SSD? Or is the difference minimal?
[/LIST]

---

### Post by gordintoronto on 2016-07-23
A 128 GB SSD is probably a boot drive, not a hybrid drive. Within Windows, there is a tool to shrink the partition, but it might not produce enough space for a useful Ubuntu installation, if the original drive is just 128 GB.

Personal prejudice: hybrid drives are a dumb idea. I recently installed a real SSD (250 GB for dual-boot), and I'm happy with it.

---

### Post by Bucky Ball on 2016-07-23
If it is two separate physical disks, an SSD and a HDD, the SSD will appear, and can be dealt with, like any other drive. In fact, I have an M.2 card, which is basically a 128Gb SATA SSD on a stick, and it appears in Gparted just like any other hard drive. You partition it exactly the same way as you would any other drive and it works just like one would. No difference. Nothing to worry about. ;)

The only difference is that the SSD is a lot faster! I only install the OS on the SSD and the rest on a HDD (personal data, /swap). A lot of us do it this way. You don't need anymore than 20Gb for the Ubuntu install on SSD and the personal data goes on the HDD.

Doing it this way, you can have many installs on an SSD. There is no reason why you need to have the OS and all your data on the same drive, SSD or HDD. I currently have my 16.04 Ubuntu install, a 14.04 install, Win7 and two partitions for virtual machines on the one SSD and I have still have 20Gb to play with (and another 20Gb reserved for the SSD ... that is the only diff really: many recommend leaving a small percentage of the SSD unallocated. Helps lengthen life apparently, but I don't know the technical details.

A modern SSD should last longer than a HDD now days, though. Hope that helps and good luck. ;)

PS: It advisable you use TRIM with SSDs. This needed to be done manually in the past. In 16.04, the trim is a cron job done once a week. There are many ways of applying trim and many opinions on which method to use. I personally just let Ubuntu do it and have never touched anything to do with TRIM manually.

---

### Post by EthioJOB on 2016-07-24
> **gordintoronto said:**
> A 128 GB SSD is probably a boot drive, not a hybrid drive. Within Windows, there is a tool to shrink the partition, but it might not produce enough space for a useful Ubuntu installation, if the original drive is just 128 GB.

Personal prejudice: hybrid drives are a dumb idea. I recently installed a real SSD (250 GB for dual-boot), and I'm happy with it.
What's wrong with hybrid drives? It's not the most straightforward, but one, they're a lot faster than hdds, and two, the price of full ssd drive is quite prohibitive. Also, increased read/write processes can shorten the life, though from what I'm hearing current ssds are rather reliable.
Also, I think 128 GB, or half if you share it with Windows, is a lot of space for just the OS (without personal data).

---

### Post by EthioJOB on 2016-07-24
> **Bucky Ball said:**
> If it is two separate physical disks, an SSD and a HDD, the SSD will appear, and can be dealt with, like any other drive. In fact, I have an M.2 card, which is basically a 128Gb SATA SSD on a stick, and it appears in Gparted just like any other hard drive. You partition it exactly the same way as you would any other drive and it works just like one would. No difference. Nothing to worry about. ;)

The only difference is that the SSD is a lot faster! I only install the OS on the SSD and the rest on a HDD (personal data, /swap). A lot of us do it this way. You don't need anymore than 20Gb for the Ubuntu install on SSD and the personal data goes on the HDD.

Doing it this way, you can have many installs on an SSD. There is no reason why you need to have the OS and all your data on the same drive, SSD or HDD. I currently have my 16.04 Ubuntu install, a 14.04 install, Win7 and two partitions for virtual machines on the one SSD and I have still have 20Gb to play with (and another 20Gb reserved for the SSD ... that is the only diff really: many recommend leaving a small percentage of the SSD unallocated. Helps lengthen life apparently, but I don't know the technical details.

A modern SSD should last longer than a HDD now days, though. Hope that helps and good luck. ;)

PS: It advisable you use TRIM with SSDs. This needed to be done manually in the past. In 16.04, the trim is a cron job done once a week. There are many ways of applying trim and many opinions on which method to use. I personally just let Ubuntu do it and have never touched anything to do with TRIM manually.

Nice. Yeah Ubuntu needs little space, though I want to keep it 40-50 GB just in case, for the future (currently my Ubuntu install is 15 GB). I don't want my options to install software to be limited. Windows though, I'm not so sure. Currently my Windows data is like this:

Windows:                                 35 GB
Users:                                      34.4 GB
Program Files:                         29.9 GB
System Volume Information:   28.1 GB

I'm not sure which ones will comprise the 'C: drive'. If possible, can you attach a screenshot of your partitions from Gparted?

---

### Post by westie457 on 2016-07-24
A standard hybrid drive is treated exactly like a normal hard drive. The 8GB SSD segment does not show as a partition or a separate drive.

See attached screenshot. 

The differences between my drive and yours should be the number of partitions and more importantly the partition-table type. Mine is the older 'msdos' type, yours should be the newer 'gpt' type.

---

### Post by EthioJOB on 2016-07-24
> **westie457 said:**
> A standard hybrid drive is treated exactly like a normal hard drive. The 8GB SSD segment does not show as a partition or a separate drive.

See attached screenshot. 

The differences between my drive and yours should be the number of partitions and more importantly the partition-table type. Mine is the older 'msdos' type, yours should be the newer 'gpt' type.
That wold make things more convenient, assuming the drive automatically configures what data goes to the ssd. Does that mean hybrid drives are made with multi-boot in mind?
Also, why do I hear other people talking about formatting and partitioning the ssd as if it was a separate drive? Are there two types of hybrid drives?

---

### Post by grahammechanical on 2016-07-24
What are we discussing? A SSD + hard drive combination? Or, a Solid State Hybrid drive (SSHD)?

[http://www.ebuyer.com/blog/2015/07/sshd-guide-to-hybrid-drives/](http://www.ebuyer.com/blog/2015/07/sshd-guide-to-hybrid-drives/)

[http://www.pcworld.com/article/2012223/hybrid-hard-drives-how-they-work-and-why-they-matter.html](http://www.pcworld.com/article/2012223/hybrid-hard-drives-how-they-work-and-why-they-matter.html)


>  Current hybrid drive designs, in contrast, deliver both technologies  within a single physical unit, and they employ software caching  algorithms (rather than relying on the user's brain) to decide which  data belongs on the SSD portion and what goes on the drive&#8217;s platters. 


  These caching algorithms reside in the hybrid drive's firmware, not the  device driver. To the computer&#8217;s operating system, a hybrid drive  appears as a single unit with the SSD portion acting strictly as a large  cache. The cache is nonvolatile, so the data doesn't disappear when  power is absent. 




Regards.

---

### Post by EthioJOB on 2016-07-24
> **grahammechanical said:**
> What are we discussing? A SSD + hard drive combination? Or, a Solid State Hybrid drive (SSHD)?

[http://www.ebuyer.com/blog/2015/07/sshd-guide-to-hybrid-drives/](http://www.ebuyer.com/blog/2015/07/sshd-guide-to-hybrid-drives/)

[http://www.pcworld.com/article/2012223/hybrid-hard-drives-how-they-work-and-why-they-matter.html](http://www.pcworld.com/article/2012223/hybrid-hard-drives-how-they-work-and-why-they-matter.html)




Regards.
Thanks for the links. They're informative. I'm not sure which drives we're talking about either as I'm more interested in the product links in my question:
[https://www.amazon.com/Dell-Inspiron-i7-6700HQ-Processor-Keyboard/dp/B01G07JUEI/ref=sr_1_4?s=pc&ie=UTF8&qid=1469277912&sr=1-4&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011&tag=gdext-20](https://www.amazon.com/Dell-Inspiron-i7-6700HQ-Processor-Keyboard/dp/B01G07JUEI/ref=sr_1_4?s=pc&ie=UTF8&qid=1469277912&sr=1-4&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011&tag=gdext-20)
[https://www.amazon.com/Dell-Inspiron-i7559-2512BLK-Generation-GeForce/dp/B015PYZ0J6/ref=sr_1_1?s=pc&ie=UTF8&qid=1469277912&sr=1-1&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011](https://www.amazon.com/Dell-Inspiron-i7559-2512BLK-Generation-GeForce/dp/B015PYZ0J6/ref=sr_1_1?s=pc&ie=UTF8&qid=1469277912&sr=1-1&refinements=p_n_feature_four_browse-bin%3A2289792011%2Cp_n_feature_seven_browse-bin%3A3012497011%2Cp_n_feature_fourteen_browse-bin%3A2057441011%2Cp_89%3ADell%2Cp_n_feature_two_browse-bin%3A5446812011)

Which drives do you think they have?

---

