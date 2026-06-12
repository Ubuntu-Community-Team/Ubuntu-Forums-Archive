---
title: "I want to install Ubuntu BUT I have already partitioned my HD"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Shaolin01 on 2008-05-25
Hi there...

I currently have partitioned my 160GB HD into 3 partitions using Acronis Disk Director.

The main partition is 20GB and has Windows XP.
The second Partition is 15GB and empty.
The third one is 115GB and empty.

I want to install Ubuntu on the 15 GB one BUT...

the installation keeps prompting me to make a partition, etc., and its all very complicated looking to me. Why isn't there just anoption to format an existing partition and install on it?

I'm probably missing something here...

Please help!

Thank you :-)

---

### Post by Pumalite on 2008-05-25
Go Manual. Delete that 15 GB partition and make 2 'New' partitions:
14 GB for '/'
The rest for /swap (/swap=RAM in laptops)
Adjust as necessary.

---

### Post by Shaolin01 on 2008-05-25
actually, my 115gb partition on that drive is not empty, it has my docs, etc.

so if i do as you say, will it affect my other partitions?

i also have a total of 1gb ddr ram on this pc.

---

### Post by Pumalite on 2008-05-25
If you do as I tell you; you'll be able to install Ubuntu and still have your 115 GB partition intact.

---

### Post by Shaolin01 on 2008-05-25
when you say delete the partition, you mean do it within the install bit of ubuntu?

---

### Post by Pumalite on 2008-05-25
After going Manual; otherwise you won't be able to create the 'New' partitions.

---

### Post by Shaolin01 on 2008-05-26
thank you for your help. i have successfully instaled ubuntu. it looks good.

i did also install the boot manager that it asked at the end of the installation, so i can choose between windows xp and ubuntu.

how can i change the boot manager so that by default it chooses to load xp over ubuntu? at the moment, the default one that it has set is ubuntu. i wuold like this to be xp for now.

thanks :)

---

### Post by Pumalite on 2008-05-26
In menu.lst; change 'dafault=0' to a number that would reflect the position of Windows in the list; keeping in mind that Grub starts counting from 0

---

### Post by The5thW on 2008-05-26
Just some feedback.  I installed this 6 times now so I think that shows some commitment.  Using your instructions, as before it does not boot up.  I dont know who this is for.  Not experienced computer users if the install is so difficult.  Can you recommend another version of Linux that will install on a second partition?

---

