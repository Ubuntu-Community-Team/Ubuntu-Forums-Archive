---
title: "Multiple Boot with Win98, WinXP, Fedora Core 5 and Ubuntu"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by vhasun on 2007-10-01
Dear All,

My primary hard is having the following partition layout. Grub is already installed by FC5 and I like to keep that.

IDE Harddrive(80GB)
       |
        ---Primary Partition (20GB) - FAT32 - Win98
       |
        ---Extended Partition (60GB)
                      |
                       ---Logical Drive(20GB) - NTFS - WinXP System
                      |
                       ---Logical Drive(20GB) - NTFS - Data
                      |
                       ---Logical Drive(2GB) - Swap
                      |
                       ---Logical Drive(18GB) - Fedora Core 5

Now I don't really need to keep "Logical Drive(20GB) - NTFS - Data" and rather want to kill it and install Ubuntu in that space. I'm having a separate hard for my data.

Can someone  please advise me the safest way to do this. I'm a bit worried as I once tried to install ubuntu (before I installed FC5) and messed it up. To be more precise I had,

IDE Harddrive(80GB)
       |
        ---Primary Partition (20GB) - FAT32 - Win98
       |
        ---Extended Partition (60GB)
                      |
                       ---Logical Drive(20GB) - NTFS - WinXP System
                      |
                       ---Logical Drive(20GB) - NTFS - Data
                      |
                       ---Logical Drive(20GB) - Free Space

I booted with the Ubuntu live CD and asked it to install in the free space (automatic partitioning). When I booted the partition setup had changed to,

IDE Harddrive(80GB)
       |
        ---Primary Partition (20GB) - FAT32 - Win98
       |
        ---Extended Partition (60GB)
       |              |
       |               ---Logical Drive(20GB) - NTFS - WinXP System
       |              |
       |               ---Logical Drive(20GB) - NTFS - Data
       |              |
       |               ---Logical Drive(2GB) - Swap
       |
        ---Partition with Ubuntu

Ubuntu installed Grub, but my WinXP was corrupted.

Is this a issue with me trying to install Ubuntu in a logical drive? But Fedora does that nicely....

I would highly appreciate if someone could advise me of what went wrong and how to replace my data partition in the safest way. thanks in advance...

regards,
uditha

---

### Post by Herman on 2007-10-01
Hello vhasun :)

>  Is this a issue with me trying to install Ubuntu in a logical drive? But Fedora does that nicely.... No, there shouldn't be any issues with installing Ubuntu in a logical partition, I have done that lots of times and never had any problems at all, Ubuntu does that very nicely. :)
>  Ubuntu installed Grub, but my WinXP was corrupted. Really? XP was corrupted? :confused: How? What exactly do you mean? Corrupted in what way?
> I would highly appreciate if someone could advise me of what went wrong and how to replace my data partition in the safest way. thanks in advance... I would do some reading in the following website first, [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
Especially this page: [Install Desktop CD Ubuntu]("http://www.psychocats.net/ubuntu/installing")
Then when you know what you are doing, just boot the Ubuntu LiveCD and install Ubuntu in the partition you want. It should be perfectly straight-froward and simple. :)
If there is something you still can't understrand or don't feel sure about please ask again for help and state your specific question, and someone here will be pleased to help you. :)

It would be a waste if time to try to guess what might have gone wrong the first time you tried installing Ubuntu. The only way is to go ahead and take a little risk and install it, then if everything doesn't turn out the way you want, come back here and ask a specific question for help. The reason is because it will be necessary to get you to run certain tests in order to give you accurate help, such as a copy of the output from 'sudo fdisk -lu', and other things like that.
Otherwise it's a lot like calling a mechanic and saying "my car won't go", without providing any clues about if it's out of gas (petrol), or oil, or the radiator has been run dry or what? it could be anything.... -same thing with computers. It's too late now for anyone to be able to tell what problem you might have had. :)

Simply try again and good luck and hopefully this time everything will go perfectly for you. :)

Regards, Herman :)

---

