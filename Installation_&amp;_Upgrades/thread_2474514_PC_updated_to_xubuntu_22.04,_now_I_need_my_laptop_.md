---
title: "PC updated to xubuntu 22.04, now I need my laptop updating to match."
date: 2022-05-01
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2022-05-01
Having successfully updated from 21.01 to 22.04 and am very happy with the result, I want the same on my laptop.

I normally try to keep the laptop as far as reasonable, a copy of the PC. Then when I travel I can upload the changed data to the PC.

If I install a fresh copy of 22.04 on the laptop and DON'T keep my /home folder data, could I copy the PC /home data to the laptop? I would then only need to install the programs which would pick up the /home data?

Possible? Practical?

I use the PC and the laptop both dual boot with windows.

---

### Post by ActionParsnip on 2022-05-01
Should be OK. If its a new installation then you have nothing to lose.
Are you replacing user data too? It would be a form of backup so kudos &#55357;&#56842;

---

### Post by makem2 on 2022-05-01
> **ActionParsnip said:**
> Should be OK. If its a new installation then you have nothing to lose.
Are you replacing user data too? It would be a form of backup so kudos &#65533;&#65533;

Yes, I would sync whatever I think necessary or which was suggested ;-)

I was thinking of using rsync which I use at the moment to backup both machines to 2 x 1TB HD on a always on Raspberry Pi used for Torrents too.

I normally only backup TO the Pi because it is a backup. I have never used rsync to sync in both directions. However as the laptop is comparatively used rarely, I could just sync before travel TO the laptop and FROM the laptop on return. It would not be a daily thing. But as you say it could also serve as backup, justifying more often syncs TO the laptop

---

### Post by Bashing-om on 2022-05-01
makem2 - hey

rsync has my full endorsement:

My use case to backup:
```

rsync -aiv --exclude=".*" --exclude uwn /home/sysop/ /mnt/look/files/

```
where my target is mounted thus:
```

sudo mount /dev/sdb6 /mnt/look/

```

A good tutorial:
[https://www.maketecheasier.com/use-rsync-command-linux/](https://www.maketecheasier.com/use-rsync-command-linux/) <- How to Master the rsync Command in Linux

[INDENT]my bit to try and help[/INDENT]

---

### Post by Impavidus on 2022-05-02
Just make sure your user ID is the same on both computers. If you're the only (human) user, the user IDs should match. Else you may have to chown.

---

### Post by makem2 on 2022-05-02
> **Bashing-om said:**
> makem2 - hey

rsync has my full endorsement:

My use case to backup:
```

rsync -aiv --exclude=".*" --exclude uwn /home/sysop/ /mnt/look/files/

```
where my target is mounted thus:
```

sudo mount /dev/sdb6 /mnt/look/

```

A good tutorial:
[https://www.maketecheasier.com/use-rsync-command-linux/](https://www.maketecheasier.com/use-rsync-command-linux/) <- How to Master the rsync Command in Linux
[INDENT]my bit to try and help[/INDENT]


Thank you for that guidance. Am I correct that 'look' is in my case /home?

@Impavidus Yes my credentials are identical on both machines.

---

### Post by Bashing-om on 2022-05-03
makem2 - Hey ---

Sorry if I confused you or muddied the waters.

> 
Am I correct that 'look' is in my case /home?


No -- that  "/mnt/look/" is the mount point I made up for the kernel to mount the file system located on my sdb6 partition.

That 'mount point' can be from anywhere you want and named as you want. '/mnt' is just generally recommended for a external file system  and 'look' is just a whimsical reminder to myself of what the mount point is.

For specifics, may I refer you to our most excellent manual ?
in terminal:
```

man mount

```
q key to quit from the manual. (mount is a whole book unto itself).

is the mud clearer now ?


-hope this helps-

---

### Post by makem2 on 2022-05-03
> **Bashing-om said:**
> makem2 - Hey ---

Sorry if I confused you or muddied the waters.



No -- that  "/mnt/look/" is the mount point I made up for the kernel to mount the file system located on my sdb6 partition.

That 'mount point' can be from anywhere you want and named as you want. '/mnt' is just generally recommended for a external file system  and 'look' is just a whimsical reminder to myself of what the mount point is.

For specifics, may I refer you to our most excellent manual ?
in terminal:
```

man mount

```


q key to quit from the manual. (mount is a whole book unto itself).

is the mud clearer now ?


-hope this helps-

Thanks man, I comprehend :-)

---

