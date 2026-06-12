---
title: "The Ubuntu installer doesn't recognize my HDD, but nautilus and gparted do. Why?"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by scaru on 2013-08-15
The Ubuntu installer does not recognize my 1 TB HDD, only my SSD. I can still see the HDD via nautilus and I can change the partitions via gparted, but no matter what the Ubuntu installer won't recognize it. 


[IMG]http://i.imgur.com/zrUs1hb.png[/IMG] 


I've tried 12.04, 12.10, 13.04, 13.10, and Linux Mint 15; all of them have the same problem. If it matters I do currently have Windows 8 installed on one of the partitions on my HDD. 


Also, in the past I have had Ubuntu installed on this HDD so I don't know why this problem just randomly appeared.

---

### Post by sudodus on 2013-08-16
Let us start with some questions to make it easier to understand the situation and help.

- Is there a gpt partition table on /dev/sda?

- Do you have an UEFI installation of Windows 8?

- What about secure boot and fast boot?

- Is Windows hibernated or in a hybrid state (semi-hibernated)?

- Did you try with 64-bit versions?

Finally, please specify the computer: Brand name and model, cpu, ram (size) and graphics card.

Edit: see this link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by scaru on 2013-08-16
> **sudodus said:**
> Let us start with some questions to make it easier to understand the situation and help.

- Is there a gpt partition table on /dev/sda?

- Do you have an UEFI installation of Windows 8?

- What about secure boot and fast boot?

- Is Windows hibernated or in a hybrid state (semi-hibernated)?

- Did you try with 64-bit versions?

Finally, please specify the computer: Brand name and model, cpu, ram (size) and graphics card.

Edit: see this link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[LIST=1]
[*]According to gdisk it is GPT with a protective MBR
[*]Yes.
[*]secure boot and fast boot have both been disabled (allowing me to boot from USB)
[*]No, windows is completely off (shut down via the shut down button within windows, and fast boot is disabled)
[*]Yes, all of the versions I've tried have been the 64 bit versions.
[*]HP Envy with an AMD 6120, a ASUS GTX 660 (OC edition), 24 GB of DDR3 RAM composed of 2 8 gigabyte sticks and 2 4 gigabyte sticks.
[LIST=1]
[*]Note: I have had Ubuntu installed on this exact computer before, also dual booting with Windows 8, so I don't think it is a hardware issue.
[/LIST]
[/LIST]

Also, if it helps I have asked this question a few other places, where I have already posted logs and various things. So if you want to see what has already been tried look here: 

[http://www.reddit.com/r/linux4noobs/comments/1kg6tq/the_ubuntu_installer_doesnt_recognize_my_hdd_but/](http://www.reddit.com/r/linux4noobs/comments/1kg6tq/the_ubuntu_installer_doesnt_recognize_my_hdd_but/)

[http://www.reddit.com/r/linuxquestions/comments/1kg7sq/the_ubuntu_installer_doesnt_recognize_my_hdd_but/](http://www.reddit.com/r/linuxquestions/comments/1kg7sq/the_ubuntu_installer_doesnt_recognize_my_hdd_but/)

---

### Post by sudodus on 2013-08-16
Well, if you have had Ubuntu installed on this exact computer before, also dual booting with Windows 8, I don't understand.

Was it installed on that same drive, that it does not recognize?

Have you tried Boot Repair?

Have you really shut down Windows? Sometimes it is only partly shut-down. See this link [[Boot-Repair]#1038]("http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648")

Edit: But you might have a different problem. I hope some [COLOR=#ff0000]real expert on booting with Windows 8[/COLOR] will see your thread :-)

---

### Post by scaru on 2013-08-16
> **sudodus said:**
> Well, if you have had Ubuntu installed on this exact computer before, also dual booting with Windows 8, I don't understand.

Was it installed on that same drive, that it does not recognize?

Have you tried Boot Repair?

Have you really shut down Windows? Sometimes it is only partly shut-down. See this link [[Boot-Repair]#1038]("http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648")

Edit: But you might have a different problem. I hope some [COLOR=#ff0000]real expert on booting with Windows 8[/COLOR] will see your thread :-)

[LIST=1]
[*]Yeah, I'm also really confused by this.
[*]Yes, exact same drive.
[*]No, what would I do from Boot Repair? I thought that was just for when the installer worked, but it wouldn't boot up.
[*]Yes, I definitely really shut down Windows.
[/LIST]

Thanks for the help.

---

### Post by sudodus on 2013-08-16
> **scaru said:**
> 

No, what would I do from Boot Repair? I thought that was just for when the installer worked, but it wouldn't boot up.
 Thanks for the help.

You can at least run the Boot-Info script and upload the result. There are gurus that can might find your problem that way. See this link

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by scaru on 2013-08-16
Ok, I'll try that later tonight. I would like to add that I ended up wiping the HDD completely, and Ubuntu still can't recognize it. I know the HDD is good though, because A. it passed the test I ran on it and B. a live Fedora USB was able to see it and recognize it.

---

### Post by oldfred on 2013-08-16
One of the Microsoft requirements for Windows 8 is fast booting. With Intel it usually is an Ultrabook with Intel SRT which uses the SSD as a cache. I have not seen that on AMD, but would think they would also use SSD as a fast boot cache. And that is often configured as RAID and then the installer has issues. Other issues could be a drive that was gpt converted by Windows to MBR, Windows partitions needing chkdsk (or Linux needing fsck), or from Windows if you created more partitions and you converted to dynamic (LDM with gpt but same issues) partitions which do not work with Linux as they are Windows proprietary. 

Post link to BootInfo report to see more info as suggested by sudodus.

---

