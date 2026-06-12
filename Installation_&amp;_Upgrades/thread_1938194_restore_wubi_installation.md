---
title: "restore wubi installation"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by tbhatia4 on 2012-03-09
Hello 
i installed ubuntu via wubi but my widows got corrupted and had to be restored i wanted to restore wubi so i reinsatlled wubi and replaced the new root.disk with the old one but the issue i am facing is that it asks for a login password at the root screen which i am sure is being entered correctly but it says login incorrect
however after replacing the same root image with the new one its working absolutely fine kindly help me restore my original installation 
thanks in advance

ubuntu version 11.04
however i must imform that the linux image of my new installtion differs from old one is this creating the issue if so kindly help me replace the linux image as well

---

### Post by pavi_elex on 2012-03-09
Log-in as user.

type in terminal now
sudo gedit /etc/gdm/gdm.conf

Now find for AllowRoot=false  and change into AllowRoot=true and save it.

change the root password or activate the root account
sudo passwd root

---

### Post by tbhatia4 on 2012-03-10
> **pavi_elex said:**
> Log-in as user.

type in terminal now
sudo gedit /etc/gdm/gdm.conf

Now find for AllowRoot=false  and change into AllowRoot=true and save it.

change the root password or activate the root account
sudo passwd root

will give this a try and let you know

thanks 4 ur concern

---

### Post by tbhatia4 on 2012-03-10
> **tbhatia4 said:**
> will give this a try and let you know

thanks 4 ur concern

i  should do it after replacing the root.disk directly or i should upgrade my new linix image to match my old one????

---

### Post by tbhatia4 on 2012-03-13
no luck yet :mad:

---

### Post by bcbc on 2012-03-13
What do you mean by root screen? do you mean a console login, or the graphical login?

Is it possible you just forgot your password, because you can reset it very easily?

---

### Post by tbhatia4 on 2012-03-14
> **bcbc said:**
> What do you mean by root screen? do you mean a console login, or the graphical login?

Is it possible you just forgot your password, because you can reset it very easily?

its a console login screen 
as far as the password issue is concerned i'm sure that i've entered that correctly 
and even i've tried changing that but no luck yet

---

### Post by bcbc on 2012-03-14
To change the password, boot into recovery mode:
1. Select the second entry (recovery mode). Before pressing enter check it first by pressing 'E' because there is a wubi bug that may affect you. If you see the line "set gfxpayload=$linux_gfx_mode" you need to delete it, and then hit CTRL+X to boot.
2. This is supposed to boot to a read-only recovery menu. If it does you select option 3: to remount read/write. If it's a root prompt (#) then just continue to step 4.
3. Then select the root prompt (probably last option).
4. Check your username:
```
ls /home
```
5. Enter a new password for your username:
```
passwd username
```

However, this doesn't explain why you're booting to a terminal. Maybe you can first fsck the root.disk to see if there is an issue:
1. Boot windows and rename the 'old' broken root.disk to OLDroot.disk
2. Put your 'new' working root.disk back in place. (So both are in \ubuntu\disks directory
3. Boot the new ubuntu, drop to a terminal (Ctrl+Alt+T) and fsck the old one:
```
sudo fsck /host/ubuntu/disks/OLDroot.disk
```

The command is case-sensitive so if you named it oldroot.disk change as appropriate.

PS you might want to backup the root.disk before fsck'ing it, or at least copy your data off it.

---

### Post by tbhatia4 on 2012-03-17
> **bcbc said:**
> To change the password, boot into recovery mode:
1. Select the second entry (recovery mode). Before pressing enter check it first by pressing 'E' because there is a wubi bug that may affect you. If you see the line "set gfxpayload=$linux_gfx_mode" you need to delete it, and then hit CTRL+X to boot.
2. This is supposed to boot to a read-only recovery menu. If it does you select option 3: to remount read/write. If it's a root prompt (#) then just continue to step 4.
3. Then select the root prompt (probably last option).
4. Check your username:
```
ls /home
```
5. Enter a new password for your username:
```
passwd username
```

However, this doesn't explain why you're booting to a terminal. Maybe you can first fsck the root.disk to see if there is an issue:
1. Boot windows and rename the 'old' broken root.disk to OLDroot.disk
2. Put your 'new' working root.disk back in place. (So both are in \ubuntu\disks directory
3. Boot the new ubuntu, drop to a terminal (Ctrl+Alt+T) and fsck the old one:
```
sudo fsck /host/ubuntu/disks/OLDroot.disk
```

The command is case-sensitive so if you named it oldroot.disk change as appropriate.

PS you might want to backup the root.disk before fsck'ing it, or at least copy your data off it.

will give this a try and let you know 
thanks anyways

---

