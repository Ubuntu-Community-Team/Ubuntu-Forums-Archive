---
title: "How to mount/view encrypted home folder after fresh install to 14.04"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by lindude on 2014-04-07
****Hi, I was running 13.04 worked a treat. Then I upgraded to 13.10, (silly me), got stuck in login loop, so I have complete a fresh install of 14.04. Unfortunately I must have encrypted my home folder back when I installed 13.04.

I set up things myself so it is probably a mess.
                                                                    
I have a mSATA which I'm used to install the OS, /dev/sdb1    ext4                 /                      boot

I also have a HDD which has                             
/dev/sda1    extended
 /dev/sda5   ext4                /media/.....
and
/dev/sda2    linux-swap                               boot

[table="width: 500, class: grid"]
[tr]
        [td]Drive[/td]
	[td]Partition[/td]
	[td]File System[/td]
	[td]Mount Point[/td]
	[td]Flags[/td]

[/tr]
[tr]
        [td]mSATA[/td]
	[td]/dev/sdb1[/td]
	[td]ext4[/td]
	[td]/[/td]
	[td]boot[/td]
[/tr]
[tr]
        [td]HDD[/td]
	[td] /dev/sda1[/td]
	[td]extended[/td]
	[td][/td]
	[td][/td]
[/tr]
[tr]
        [td]HDD[/td]
	[td] /dev/sda5[/td]
	[td]ext4[/td]
	[td]/media/.....[/td]
	[td][/td]
	[/tr]
[tr]
        [td]HDD[/td]
	[td]/dev/sda2[/td]
	[td]linxu-swap[/td]
	[td][/td]
	[td]boot[/td]
[/tr]
[/table]

I have tried a couple of things to mount/view my folder since I installed 14.04 but without success.
[LIST=1]
[*]ecryptfs-mount-private ERROR: Encrypted private directory is not setup properly
[*]sudo ecryptfs-mount-private [sudo] password for beefcake:  ERROR: Encrypted private directory is not setup properly
[*]sudo -i encryptfs-mount-private -bash: encryptfs-mount-private: command not found
[*]sudo ecryptfs-recover-private INFO: Searching for encrypted private directories (this might take a while)... INFO: Found [/media/beefcake/ad7119ef-aaa2-4e81-a16d-9f84687dcd7f/.ecryptfs/beefcake/.Private]. Try to recover this directory? [Y/n]: y INFO: Found your wrapped-passphrase Do you know your LOGIN passphrase? [Y/n] n INFO: To recover this directory, you MUST have your original MOUNT passphrase. INFO: When you first setup your encrypted private directory, you were told to record INFO: your MOUNT passphrase. INFO: It should be 32 characters long, consisting of [0-9] and [a-f].  Enter your MOUNT passphrase:  INFO: Success!  Private data mounted at [/tmp/ecryptfs.nLVycpoH].

I also tried so many other how to without success hence the fresh install and now asking for help!
Can anyone please tell me how to make the folder part of my OS again, (read, write, etc), just like it was back when I had 13.04?

Thanks!

---

### Post by slickymaster on 2014-04-07
I would recommend that you use the [ecryptfs-recover-private]("http://manpg.es/ecryptfs-recover-private") utility.
A full explanation of how to use it is available [here]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html").

---

### Post by lindude on 2014-04-08
Thanks slickmaster for your time!
I'd already looked at it. 
I was hoping that there might be a way to use the encrypted drive with my new system, I know the password so I just figured that I should be able to login, (for want of the correct word), with it and use my drive again.
Is that possible?

---

### Post by slickymaster on 2014-04-08
Have you give [Live CD method of opening a encrypted home directory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory") a try?

---

### Post by lindude on 2014-04-10
Thanks again slickmaster.
I'll check it out.

---

