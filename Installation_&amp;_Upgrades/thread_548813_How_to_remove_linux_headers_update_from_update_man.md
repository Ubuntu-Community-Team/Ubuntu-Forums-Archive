---
title: "How to remove linux headers update from update manager?"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by Rizlaw on 2007-09-11
I am running two Ubuntu 7.04 boxes. On both boxes, I had set Synaptic Package Manager to provide me with "unsupported updates (backported feisty)". I'm not sure why I did such a foolish thing, but I did.

Recently, when I routinely installed all the listed updates on computer #1, one of the update files (linux-headers-2.6.20-16) messed up my AMD dual core cpu and said it was only a single core cpu; more importantly, it totally fragged my ability to use VMWorkstation 6. After a long back and forth on VMware's forum with a great VMWare support person, we traced the problem to the wrong linux header being installed (the one I mentioned above). The correct linux header to install was "linux-headers-2.6.20-16-generic".

Anyway, I don't want to accidently repeat the same mistake on computer #2. Computer #2 is telling me there are updates identical to what I saw on computer #1. I have already selected the correct linux header file and installed it. However, I can not find a way to get rid of the file "linux-headers-2.6.20-16" which I "unchecked" so that it would not be installed and cause me grief all over again. I also changed my settings in Synaptic Package Manger to exclude "Unsupported Updates (backported feisty)."

So after  my long winded explanation, is there a way to permanently make "Update Manager" remove this file from the list of files for update? I don't want to keep on seeing it pop up, as I might accidently leave it checked and then it will install itself and screw up my system.

Thanks for any help.

---

### Post by bmeyer on 2007-09-11
> **Rizlaw said:**
> I am running two Ubuntu 7.04 boxes. On both boxes, I had set Synaptic Package Manager to provide me with "unsupported updates (backported feisty)". I'm not sure why I did such a foolish thing, but I did.

Recently, when I routinely installed all the listed updates on computer #1, one of the update files (linux-headers-2.6.20-16) messed up my AMD dual core cpu and said it was only a single core cpu; more importantly, it totally fragged my ability to use VMWorkstation 6. After a long back and forth on VMware's forum with a great VMWare support person, we traced the problem to the wrong linux header being installed (the one I mentioned above). The correct linux header to install was "linux-headers-2.6.20-16-generic".

Anyway, I don't want to accidently repeat the same mistake on computer #2. Computer #2 is telling me there are updates identical to what I saw on computer #1. I have already selected the correct linux header file and installed it. However, I can not find a way to get rid of the file "linux-headers-2.6.20-16" which I "unchecked" so that it would not be installed and cause me grief all over again. I also changed my settings in Synaptic Package Manger to exclude "Unsupported Updates (backported feisty)."

So after  my long winded explanation, is there a way to permanently make "Update Manager" remove this file from the list of files for update? I don't want to keep on seeing it pop up, as I might accidently leave it checked and then it will install itself and screw up my system.

Thanks for any help.

You could just let it do the update, but then remove the 2.6.20-16 from Grub.
```
sudo gedit /boot/grub/menu.lst
```

Comment out all the lines in there dealing with 2.6.20-16.  This obviously doesn't remove the kernel version from your system -- it just blocks it from being booted up.  I had the same issue as you and this was my work around.

---

### Post by Pumalite on 2007-09-11
It might be:
gksudo gedit /boot/grub/menu.lst

---

### Post by dcstar on 2007-09-12
> **Rizlaw said:**
> 
........
So after  my long winded explanation, is there a way to permanently make "Update Manager" remove this file from the list of files for update? I don't want to keep on seeing it pop up, as I might accidently leave it checked and then it will install itself and screw up my system.

Thanks for any help.

It is extremely simple - go into Synaptic, find the package you **don't** want to change, select it and go to: Package-Lock Version and tick the box.

Now that package will be fixed at that version and ignored by the Update Manager, but all your other (Unpinned) packages can be updated as normal.

---

### Post by Rizlaw on 2007-09-12
> **dcstar said:**
> It is extremely simple - go into Synaptic, find the package you **don't** want to change, select it and go to: Package-Lock Version and tick the box.

Now that package will be fixed at that version and ignored by the Update Manager, but all your other (Unpinned) packages can be updated as normal.

Thanks dcstar, that worked quite nicely.:)

I thought there had to be a simple way to do this without resorting to installing the unwanted update.

It seems to me this should be a tick box option in "update manager". Only an advanced Ubuntu user is going to know that it can be done within Synaptic.

Thanks also bmeyer for your workaround suggestion.

---

