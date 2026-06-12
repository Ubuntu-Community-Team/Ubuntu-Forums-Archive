---
title: "Experts only strangest case ever explanation needed"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by slythecooper on 2012-01-15
hi there, 
let me just give you a bit of a background. I am fairly good with linux and have used RH and openSUSE before in the past. I tried to install ubuntu (dual boot with w7, i gave Ubuntu 40gb), but however got a problem with the installation and it accidentally installed on D drive. i could not boot into ubuntu, and it took 40 gb out of the drive. I messed around with the ext3 partition created by installation with ext 2 volume manager. Then i chose to install ubuntu again, and i chose the noob option install alongside w7. HOWEVER, it did not give me the option to choose disk space and went directly to the installation process. I thought i was going to loose w7. But however by some miracle it managed to keep both. Now this is the funny thing. You know when you boot normally, you have that black and white screen with the two options winddows or ubuntu (assuming that you have it installed) and when you press ubuntu you get that purple screen with two options (or something like that, i got Linux debian and recovery mode with wubi) Now when i boot my computer it goes DIRECTLY onto the linux boot option. AND I STILL GET THE OPTION TO BOOT ONTO WINDOWS! with an option called w7 loader sda1, along with two other options memory check and mem check x64. Nothing has changed in W7 (data everything still intact) except for the fact that i have 2 new drives in My Computer, one with an ext3, with all my linux files (I CAN BROWSE THROUGH IT ON WINDOWS!!) and one blank ntfs with 3.99 GB CAPACITY (the other is 34GB Capacity)

so in all, can anyone tell me what is going on right now and what should i do.

Slythecooper

---

### Post by Paddy Landau on 2012-01-15
That's quite an essay, and I'm not quite sure I understand what you wrote. I also find your title quite confusing.


[LIST]
[*]Did you uninstall WUBI before you tried to install dual-boot?
[/LIST]

[LIST]
[*]Did you remove the first Ubuntu installation (on what you call your D drive) before you tried the second installation?
[/LIST]

[LIST]
[*]Please boot into Ubuntu, open a terminal, type the following command and post the results here (between [noparse]```
[/noparse] and [noparse]
```[/noparse] please).```
sudo parted --list
```That will give us some idea of what is happening on your drives.
[/LIST]

---

### Post by slythecooper on 2012-01-15
First of all i am sorry if my english is very bad (i am new to this language and i am using Google Translate) so i am not sure how good this will be in English for you non english speakers. 

1) no i not have wubi installed on this computer
2) i not sure if i uninstall completely, i took the partition on ext2 volume manager, changed the ext3 to ntfs and formatted it via windows.
3) i will get right onto the sudo command and will post results later.

Many Thanks

---

### Post by Paddy Landau on 2012-01-16
I understand that you do not speak English.

I will try to use simple language.

Windows prefers NTFS.
Ubuntu prefers ext4.

I await your reply.

---

