---
title: "What does it mean???"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by unfaigui on 2006-12-08
Hi everyone
I would like to know what this command line mean:
"[COLOR="Red"]root@sahara:/var/lib/tftpboot/ubuntu/edgy$ 
mount -o loop edgy-alternate-i386.iso alternate/[/COLOR]"

I am trying to install ubuntu on localnet but install page told me to "Mount the CD (media or image) under the tftpboot dir" with that command line I showed you above.

Also there are couple questions i am not quite sure in the above command.
1.Is there a folder called "/var/lib/tftpboot/ubuntu/edgy/alternate" ?
2.Where is the "[COLOR="Sienna"]edgy-alternate-i386.iso[/COLOR]" file located? Is it located on the cd or in the folder called "/var/lib/tftpboot/ubuntu/edgy/alternate"?
3.What does it mean by "loop device"?

I hope you guys will able help me to understand these.
thanks

unfaigui

---

### Post by Hendrixski on 2006-12-08
To "teach a man how to fish" as the saying goes...

type in "man mount" into the terminal, and it'll tell you what the mount command does, and what the -o option means.

and, sigh*,  there are of course 100 nerdy jokes about the mount command.

---

### Post by meng on 2006-12-08
The bit before the $ is not part of the command of course, it is just the command prompt telling you username@host:/current/working/directory$
And quickly,
mount          means you're trying to mount a filesystem to some location so that you can access the filey goodness within
-o loop        means it's a loop device not a block device
edgy[blah].iso    is the file(system) you're trying to mount
alternate/        is the location you're trying to mount to, in your case you're mounting relative to your current working directory, i.e. to /var/lib/tftpboot/ubuntu/edgy/alternate

I usually chuck in
-t iso9660
just for completeness, since you're mounting an ISO (CD image)

e.g. mount -t iso9660 -o loop [isoname] [location]

---

### Post by unfaigui on 2006-12-08
Thanks a lot Meng for your explanation. I understand what that command does now.

To Hendrixski, I was trying to read the man page of mount but i don't understand what it is. But i will try to read and understand it in the future. On the man page, it should have more example how to use the command for someone very new in the linux world.

thanks to everyone.
unfaigui

---

