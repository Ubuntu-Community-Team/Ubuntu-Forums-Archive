---
title: "Problem when changing password of luks encrypted partitions created in MFSE"
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by ranloe on 2018-06-04
This is a problem I encountered when trying to change the password for my encrypted luks partitions (system & data) created with the ManualFullSystemEncryption guide by Paddy Landau ([https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)).  my setup is slightly different than the one illustrated in the guide, and I have had custom instructions from paddy before in the following thread: [https://ubuntuforums.org/showthread.php?t=2357978](https://ubuntuforums.org/showthread.php?t=2357978)

  I am running a laptop with dual boot Ubuntu 16.04 and Windows 10. I fully encrypted the ubuntu part using the above mentioned guide and have been using this setup successfully for over a year. Today I wanted to change the password for my Ubuntu Encryption. I did the following:

  I booted into my pc using a LIVE usb with ubuntu on it. I then opened Gparted to see the names (e.g. sda1) of my "system" and "data" partition. I did what follows for each partition:
 I  ran `sudo cryptsetup luksDump "partitionname"` which showed me that both Slot 0 and Slot 1 were ENABLED. I proceeded with `sudo cryptsetup luksAddKey "partitionname"` which filled up Slot 2. Next, I deleted Slot 0 and 1 with `sudo cryptsetup luksKillSlot "partitionname" "slotnumber"`. luksDump now showed 0 and 1 DISABLED and only slot 2 ENABLED.  On the LIVE usb i could now unlock both partitions with my new password, and that one only. I then rebooted and removed the LIVE usb, but when enterening the new password on the usual 'unlock encrypted volume' screen, the new password doesn't work.

  I then went back to study the  ManualFullSystemEncryption guide to find out if there could be a clue there and sure enough, under 7.1.1 -  2. on [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt) was written the following:  "(At this point, the system will allow you to add up to eight users, but you must leave one free, because it is used later in these instructions.)" 
this message is given after a luks encryption password has alrdy been created under  7.1 and I believe that the slot that is referred to as being "used later in these instructions" is the one filled in point "3. Create key files" on this page: [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces)

To summarize, I believe the booting process set up using the ManualFullSystemEncryption guide needs 2 passwords, set up during the guide. However, I broke the booting process by deleting both the one i was actively entering each time when booting (also being the one i set manually during the booting process) and the one that was created with `sudo cryptsetup luksAddKey /dev/sdA5 /mnt/root/etc/crypt.system` (under "3. Create key files").  
Thank you for your time and consideration.

---

### Post by Paddy Landau on 2018-06-05
Thanks for posting your query.

Let's back up a little. The installation uses the following slots.
[LIST]
[*]Slot 0: Your passphrase.
[*]Slot 1: The key for automatic system decryption (*after* you have already entered your passphrase). You created this key in [Create key files]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Create_key_files"), and the system most importantly uses it to decrypt your data partition so that you have to enter only your system passphrase each time you boot.
[/LIST]

You said that you wanted to change your passphrase. I don't know why you didn't do that, instead of adding a new passphrase and deleting the existing ones, but never mind — let's fix what you've done.

You merely need to resurrect the keys for automatic system decryption.

[LIST=1]
[*]Boot from your Live USB.
[*]Decrypt your LUKS system partition using your new system passphrase. This step comes from [Unlock your partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Unlock_your_partition"). You can skip the part to decrypt your data partition. Remember to change [FONT=lucida console]sdA5[/FONT] accordingly.
```
sudo cryptsetup luksOpen /dev/sdA5 system
```
[*]Mount your system partition. These two lines come from [Mount partitions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Mount_partitions") (skip the bits to mount [FONT=lucida console]/boot[/FONT] and your data partition).
```
sudo mkdir /mnt/root
sudo mount /dev/mapper/system-root /mnt/root
```
At this point, your keys for your system and data partitions reside in [FONT=lucida console]/mnt/root/etc/crypt.system[/FONT] and [FONT=lucida console]/mnt/root/etc/crypt.data[/FONT] respectively.
[*]Reload the keys for each of your partitions. The next two lines come (again) from [Create key files]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Create_key_files"). Remember to change [FONT=lucida console]sdA5[/FONT] and [FONT=lucida console]sdB1[/FONT] accordingly.
```
sudo cryptsetup luksAddKey /dev/sdA5 /mnt/root/etc/crypt.system
sudo cryptsetup luksAddKey /dev/sdB1 /mnt/root/etc/crypt.data
```
[/LIST]
Finally, reboot to check if this has worked.

I've never done this, so I hope that it works. Please post back here to let us know what happens.

[SIZE=3]**Next time**[/SIZE]

If you wish to change your passphrase, use the following commands. If I recall correctly, you don't have to boot from a Live USB to do this; you should be able to do it from your normal system. Again, be sure to change [FONT=lucida console]sdA5[/FONT] and [FONT=&amp]sdB1[/FONT] accordingly. The command [FONT=lucida console]luksChangeKey[/FONT] prompts you for your current passphrase, which is how it knows which slot to change.
```
sudo cryptsetup luksChangeKey /dev/sdA5
sudo cryptsetup luksChangeKey /dev/sdB1
```

---

### Post by ranloe on 2018-06-05
I followed your instructions and got the same error message.

Previously when following your guide, the only problem i had encountered was that i'd entered my luks passphrase while ubuntu was configured to use azerty keys, but when I had to enter the passphrase while booting, there is no option to change the keyboard layout. I'd solved that by simply going back and changing the keyboard layout to qwerty US when creating the luks passphrase. 

When I'd created the new passphrase that led to my current problem, I'd done the same thing, so I assumed there could be no mix up because of the different keyboard layouts. Nevertheless, my password was quite complicated so i decided to try and add a 1 letter passphrase to make sure once and for all that I wasn't just entering something wrong when booting. This solved the problem. I proceeded to configure cryptsetup from within my ubunutu workstation, first adding a secure password that i was sure i could enter correctly when booting, then, after i'd verified that, using luksRemoveKey to remove both the 1 letter passphrase and the faulty one.

Thank again for all your help Paddy. You're a Hero !

---

### Post by Paddy Landau on 2018-06-05
Yes, keyboards can be a problem! For that reason, try to stick to using only letters, digits and punctuation that you'll find on all common keyboards. Of course, the meaning of "common" varies by location.

Please would you [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") — thanks!

---

