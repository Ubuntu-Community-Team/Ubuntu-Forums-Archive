---
title: "Grub File Error"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by sougata on 2015-08-09
Dear All, 

I am facing grub issue and I am trying to fix it all day but failed. I have gone through endless posts but still couldn't find the right answer. I am seeing blank screen with grub rescue command prompt. I am doing the below steps 

1. grub rescue> ls

(hd0)(hd0,msdos6)(hd0,msdos5)(hd0,msdos1)

2. When I run,

ls (hd0)/boot/grub

Error Unknown file system 

Same response for hd0,5 and hd0,1

3. So.now when I run this command,

ls (hd0,6)/boot/grub

Error file not found

4. Now I run the set command

grub rescue> set

Prefix=(hd0,msdos1)/boot/grub

Root=hd0,msdos1

But when I run " ls (hd0,msdos1)/boot/grub" I still get error unknown filesystem.

5. I go ahead to set a new prefix and root and run the commands

Set prefix=(hd0,msdos6)/boot/grub

Set boot=(hd0,msdos6)

Insmod normal

Error file.not found

6. Now when I again run the set command.I see the.new prefix and the.new boot but surprisingly I still see the old root.

I am completely lost how to fix this issue.

Kindly help

Cheers,

Sougata

---

### Post by Bashing-om on 2015-08-09
sougata; Hello;

The boot process is of interest to me. Between the two of us I bet we can figure out what the root of the problem is.

In my troubleshooting procedure, I want to know where grub's config files are located:
What returns:
```

search -f /vmlinuz
search -f /sbin/init

```
From the above we know we have several possibilities of which partitions the config files may be located.
Once we know the location of the config files, we can tell grub where to look, and grub can pass on the the kernel where the kernel's files are located. We get this sucker booted and repair grub .

caveat: if the config files are corrupted, well, we must purge and rebuild them . With a liveDVD is no big deal .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sougata on 2015-08-09
@Bashing-om Thanks a lot for your response. So to fix this situation do i need to have a installer CD? Mine one is 12.04 LTS. As of now I don't have the CD...:( Because after going through so.many blogs or responses regarding this kind of situation either I am seeing people fixing his problem with an installer CD or their grub files are easily located. Not like my situation where I can see 4 partitions and out of them 3 clearly says unknown file system but the 4th one says file Not found.

Just to clarify without CD is it possible to look for the files? I mean commands are so less in this rescue mode that it is giving me troubles.....

---

### Post by Bashing-om on 2015-08-09
sougata; Hey;

Maybe .. Boot back into the install to the grub rescue > prompt.
At this prompt what returns:
```

search -f /vmlinuz
search -f /sbin/init

```

Hoping to make the seeking for the config files an easy matter, Else we do it one partition at a time .

[INDENT][INDENT]boot it
[INDENT][INDENT][INDENT]sometimes is an art
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sougata on 2015-08-10
Ok so am tying to run both of these commands in the grub rescue but it says unknown command search... :(

---

### Post by Bashing-om on 2015-08-10
sougatal Yuk;

I guess 'grub rescue > ' is a bit more limited in what commands are available than is 'grub >' .
Back to hunting:
```

ls -lh (hd0,msdos1)/boot/
ls -lh (hd0,msdos5)/boot/
ls -lh (hd0,msdos6)/boot/

```
where we are looking for the grub directory, the initrd.img and vmlinuz files. These are all at the same location.

This is a single hard drive system, yes ? Such that the boot files we seek are on this hard drive [(hd0)].

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by sougata on 2015-08-10
Ok so I am applying all these commands and it gives me only one reply which is unknown file system..:(

Also why 2 different responses for the below mentioned 2 commands

grub rescue> ls -lh (hd0,msdos6)/boot/
Error unknown filesystem

grub rescue> ls (hd0,msdos6)/boot/grub
Error file not found

Yes its a single OS machine. I am running LTS 12.04

---

### Post by Bashing-om on 2015-08-10
sougata; Yuk;

1st things first:
> 
Ok so I am applying all these commands and it gives me only one reply which is unknown file system..


Means we have no other alternative than to boot up a liveDVD and run a file system check/repair.
If the file system is intact, then we look at re-installing grub when we know what the partitioning is; such that we can direct grub where to install it's config files.

As to:
> 
grub rescue> ls -lh (hd0,msdos6)/boot/
Error unknown filesystem

Here we are looking for a directory ( /boot/).

and here:
> 
grub rescue> ls (hd0,msdos6)/boot/grub
Error file not found

we are looking for the files contained in the directory (grub) .
It might prove interesting if we implicitly direct that a search be done for the exact directory, declaring that 'grub' is a directory. 
Like so:
```

grub rescue> ls -lh (hd0,msdos6)/boot/grub/

```
Here where the trailing '/' in '/grub/' declares to the system this is a directory that we want the contents of.

As the file system is corrupt, the system is unable to comply.

And, We are back to requiring a liveDVD to mount the installed file system and have a looksee as to what we can do to repair .
This liveDVD [ or a USB ] must be the same same release as that of the installed operating system.

when one tool does not work
[INDENT][INDENT][INDENT]we pick up another
[/INDENT][/INDENT][/INDENT]

---

