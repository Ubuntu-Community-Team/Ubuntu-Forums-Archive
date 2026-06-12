---
title: "Internal Hard Disk not mounted"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by awam66 on 2008-07-29
I recently had intrepid running on my 80G external USB drive which I had installed using the upgrade path.  Unfortunately the disc crashed the other day and became unusable, so I downloaded the Alpha 3 alternative iso (AMD64) and installed on the same disc after reformating. Everything went OK except that now when using Intrepid I cannot access the internal hard drive. It fails to be detected, but has Hardy installed on it. The installation found the internal drive because it is shown in grub's menu.lst. Any ideas please.

Dell Dimension C521 AMD athlon 64 processor 250G internal hard drive

---

### Post by Gina on 2008-07-29
Nautilus is having trouble mounting things.  This is currently being investigated.  Try using the mount command from a Terminal.

---

### Post by awam66 on 2008-07-29
> **Gina said:**
> Nautilus is having trouble mounting things.  This is currently being investigated.  Try using the mount command from a Terminal.

Thanks Gina, but I'm not sure what the parameters are for mounting the drive. It doesn't show in mnt but does in dev.

---

### Post by taavikko on 2008-07-29
make dir to mount it in.
```
sudo mkdir /media/example
```

then mount it
```
sudo mount /dev/sdxx /media/example/
```


```
man mount
```
tells more.

---

### Post by awam66 on 2008-07-29
Yes I tried that and it mounted OK I think, but I still can't access it.

Just got back from being out. Booted up and tried again.
This time it mounted OK but appeared twice. I believe though that is a known bug.

---

### Post by taavikko on 2008-07-30
> **awam66 said:**
> Yes I tried that and it mounted OK I think, but I still can't access it.

Just got back from being out. Booted up and tried again.
This time it mounted OK but appeared twice. I believe though that is a known bug.

Yep, known bug, That mount command only mounts the partition/drive for an session. For more permanent solution, you need to edit /etc/fstab
to make it mount on boot.

Or did you mean you dont have rights to do anything, on that partition?
that can be fixed by 
```
sudo chown -R $USER:$USER /media/foldername
```

---

### Post by jfernyhough on 2008-07-30
> **taavikko said:**
> 
```
man mount
```
tells more.Just BTW, don't do a Google search for that.

---

### Post by awam66 on 2008-07-30
> **taavikko said:**
> Yep, known bug, That mount command only mounts the partition/drive for an session. For more permanent solution, you need to edit /etc/fstab
to make it mount on boot.

Or did you mean you dont have rights to do anything, on that partition?
that can be fixed by 
```
sudo chown -R $USER:$USER /media/foldername
```

I'm ok with rights but Im not sure what to put in fstab.

The funny thing is if I do a mount for stb1 which is the usb drive it mounts it but it is already mounted as that is the active disk. If I then do mount sta1 which is the internal drive it mounts it as well.

---

