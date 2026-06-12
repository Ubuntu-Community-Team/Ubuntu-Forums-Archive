---
title: "Installing over a previous distribution"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by Quidam29 on 2010-06-17
I just received a CD to install Ubuntu. I already have a Linux distribution installed (Mandrake 10). 
Is it possible to replace Mandrake with Ubuntu and keep all my files or do I have to save them and import them after installing Ubuntu?

---

### Post by irv on 2010-06-17
A couple of question. Do you have your /home/"username" on it own partition? If not then you need to backup your files and then bring them back after a fresh install of Ubuntu. Or are you planning to do a dual boot with the other OS? If so you will be able to get at the files after installing Ubuntu. And the last question; is your hard drive big enough to install both OS's?

Edit: what ever you do backup your file first.

---

### Post by Quidam29 on 2010-06-17
I do have home on its own partition but is it the same as /home/"username. I do not want dual boot with mandrake but with Windows yes which I already have. If I have to back up, where do I back up since the disk will be erased? I have a flash disk but it doesn't take linux files as far as I know.

---

### Post by irv on 2010-06-17
> **Quidam29 said:**
> I do have home on its own partition but is it the same as /home/"username. I do not want dual boot with mandrake but with Windows yes which I already have. If I have to back up, where do I back up since the disk will be erased? I have a flash disk but it doesn't take linux files as far as I know.

I would think the flash drive is readable in Linux. Are your files in Windows and Linux? If so just backup from both OS's on the flash drive. Remove the flash drive before installing so you do not accidentally destroy your backups.
When you go to install Ubuntu, it will ask if you want to install alongside the other OS's, if you say yes you will keep what you have and install Ubuntu. You will end up with three OS's. If this is not what you want (only Windows and Ubuntu) you will need to manually partition you Hard drive and if this is the first time you are doing this you may need help with this. 
You may want to do a little reading: Start here:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by garvinrick4 on 2010-06-17
> **Quidam29 said:**
> I do have home on its own partition but is it the same as /home/"username. I do not want dual boot with mandrake but with Windows yes which I already have. If I have to back up, where do I back up since the disk will be erased? I have a flash disk but it doesn't take linux files as far as I know.
It will take Linux files. If you want to format as Fat32 which it most likely is anyway.
As long as the /home is on a seperate partition and you do not reformat it, it will retain
your files. Just put Ubuntu in the same sdaX that you are using now for / install.

---

### Post by Quidam29 on 2010-06-17
Thank you to RV and Garvinrick4 for the quick reply. This should give me enough to get it done I think

---

### Post by wojox on 2010-06-17
Even with /home on a separate partition I would still back it up.

---

### Post by gadolinio on 2010-06-17
> **garvinrick4 said:**
> It will take Linux files. If you want to format as Fat32 which it most likely is anyway.
As long as the /home is on a seperate partition and you do not reformat it, it will retain
your files. Just put Ubuntu in the same sdaX that you are using now for / install.

> **wojox said:**
> Even with /home on a separate partition I would still back it up.

I agree with both.
Backup your files, just in case. It's a good practice before this kind of task.
And just install ubuntu in mandriva's partition.

---

