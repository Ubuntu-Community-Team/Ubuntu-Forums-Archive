---
title: "dpkg: error: cannot access archive"
date: 2023-04-19
forum: Installation &amp; Upgrades
---

### Post by ttgteacher on 2023-04-19
I am running Ubuntu 22.04.2 LTS 

When I update and upgrade, I get the following error:
```
dpkg: unrecoverable fatal error, aborting:
 loading files list file for package 'fonts-tibetan-machine': cannot read /var/lib/dpkg/info/fonts-tibetan-machine.list (Input/output error)
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

I cannot use Firefox, and my PC is not working right, can anyone help me? Thank you!

---

### Post by #&amp;thj^% on 2023-04-19
Please, Please use normal fonts.
can you show us this:
```
ls /var/lib/dpkg/info/ | grep fonts

```
EDIT: and one more while we are here:
```
ls -l /var/lib/dpkg/status*

```

---

### Post by Impavidus on 2023-04-19
Multiple errors that have nothing directly to do with each other, at least one give an I/O error on file access... That smells like a damaged filesystem, possibly a broken harddrive.

Can you test smart status of your hard drive? BTW, best to monitor that over time.

---

### Post by MAFoElffen on 2023-04-19
[QUOTE=ttgteacher;14139676]I am running Ubuntu 22.04.2 LTS 

When I update and upgrade, I get the following error:
```

... [COLOR=#ff0000]cannot read[/COLOR] /var/lib/dpkg/info/fonts-tibetan-machine.list ([COLOR=#ff0000]Input/output error[/COLOR])

```
When I saw this in the first post, the first thing I thought of was;

Reboot the machine and at the Grub2 menu, use Advance Options > Rescue > fsck. If it is just an EXT filesystem error, it will attempt to repair it. If it is a bad part of the disk, it will attempt to move it to a good part of the disk and mark that sector as bad. The same with ZFS ZPool scrub for filesystems on ZFS.

If it says that it had to repair the filesystem and there is still a problem with reading that file, then reinstall the package via
```

sudo apt install --reinstall fonts-tibetan-machine

```
I recognize that as a font package for Tibetan, Dzongkha and Ladakhi.

I may be confused, but... Everyone lately seems to jump directly to smartmontools first for reading errors (which I use), but seem to forget that there are other tools to use first. That, and smartmontools is not a default installed application and so it would need to be installed by a User before using it.

I love smartmontools and it is invaluable for what it does, and what it can report... now, along with nvme-cli for NVMe drives. I use both a lot.

Just my thoughts.

---

### Post by ActionParsnip on 2023-04-20
I suggest you boot to Ubuntu liveCD / ISO / USB and run an fsck against the internal file systems to make sure they are healthy

---

### Post by ttgteacher on 2023-04-20
I tried, but this did not work.

---

### Post by ttgteacher on 2023-04-20
I tried this, but had no success.

---

### Post by Bashing-om on 2023-04-20
ttgteacher; Hello

> 
I tried, but this did not work.

is devoid of information and does no tell us anything new.

What did you try and what is the result - exactly ? What did you look forward to happening ?

[INDENT]with a free operating system
[INDENT][INDENT]we move the world
[/INDENT][/INDENT][/INDENT]

---

### Post by ttgteacher on 2023-04-21
[SIZE=4]I followed the instructions above and typed this into terminal, hoping my system would update, and upgrade. I still got the same error, and my pc does not work properly. 

I just need simple to follow instructions from someone in the forum who knows how to help me. Do you think I should try something else? I am looking to see what I can do to remove the error message and be able to use my computer.

Thank you! [/SIZE]
[SIZE=4]
[/SIZE]
[SIZE=4]ls /var/lib/dpkg/info/ | grep fonts
ls -l /var/lib/dpkg/status*[/SIZE][SIZE=4]sudo apt install --reinstall fonts-tibetan-machine
[/SIZE]

---

### Post by ttgteacher on 2023-04-21
[SIZE=5]**Thank you all, I reinstalled 22.04.2 LTS, I appreciate your help. I lost all my files, pictures and documents, but I am back up and running. :)**[/SIZE]

---

