---
title: "Grub error 17  - somebody help please"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by beko on 2006-06-07
Hi ... I have a problem which is making me very disappointed from Ubuntu 6.06 because It took a very long time to be released & finally came out with like this bug.

My problem is that I have 2 hard drives one is Sata 160 GB  & the other one is IDE 20 GB ( I use it just to be between linux & windows since I can't write to NTFS from linux) I used to have Suse 10.1 retail version( just bought since 2 weeks) Daul boot with windows XP.

I use 35 GB from the Sata hardrive for it & it was working fine but since I used to work with Ubuntu before I buy it & after I saw 6.06 just came out I couldn't stay like this without trying it so I just deleted the suse partations & used the 6.06 Desktop cd to install & really everything went fine untile the process finished & I took out the cd & expected to see the grub menu with UBUNTU 6.06 & Windows xp but grub looked like it's going to start then give me error 17 .

I tried to even goto the command line but I couldn't so I decided to take a look here & I found many people have the same issue but I didn't find any way to fix this untile now.

Now I had to restore my mbr to windows xp so I will be able to post this thread maybe somebody have any idea about what should I do, I can just go back to Suse 10.1  but I will be always thinking that I couldn't try Ubuntu 6.06 .

Please advise.

---

### Post by wfx on 2006-06-07
about error 17 does grub say:
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB

Can you write it down like a table (maybe i can better folow it :-))?
HD xy  | Partition | Operating System

Maybe youre root point to the wrong device, it sounds
to a wrong root(hd0,x) setup.

We can try it out with grub itself
# Power on
# Press [Esc]
# Press e (edit)
# Go to the line similary "root (hd0,0)
# and change the device 

Damm you have remove the grub boot :-)
So you need a bootdisk with a grub menu
with tis bootdisk we can restore the bootmanager (2 comands) and try out the above

---

### Post by beko on 2006-06-07
Thank you for your answer, I think this is a common bug in the (desktop cd ) I decided to try the altrnative CD & from the Text mode everything went fine so in case anybody have the same problem I suggest to try the altrnative CD.

---

