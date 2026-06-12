---
title: "Not copying from hard drive"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by bocmaxima on 2007-02-03
Heres my dilemma. I have a 160gig HD that is NTFS partitioned, and I want to use it to backup my stuff so i can do a wipe/install of edgy (needs it anyway)...however, I cant just format the drive, cause I need to get some stuff off there. I have it mounted and everything, but when i try and drag the filesinto a folder on my desktop, nothing happens. I know I should be able to do this because I did it before when i pulled my music off. Anyone know what why I cant copy things?

---

### Post by meng on 2007-02-03
You can't write to an NTFS partition by default, you only have read access. If you must have read-write access, you need to install/enable ntfs-3g (search the forums for an ntfs-3g howto).

---

### Post by finer recliner on 2007-02-03
possibly file permissions [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

read this, and make sure that the windows partition is allowing you to read and execute from it (dont give write permissions to an NTFS drive though)

---

### Post by bocmaxima on 2007-02-03
> **finer recliner said:**
> possibly file permissions [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

read this, and make sure that the windows partition is allowing you to read and execute from it (dont give write permissions to an NTFS drive though)


Cool, ill try that, i do know that execute is disabled.

---

### Post by bocmaxima on 2007-02-03
I changed permissions, but its still not doing anything...:/

---

### Post by meng on 2007-02-03
Hey there - did you read my post? I wouldn't blame you if you hadn't, lots of folks seem to be ignoring my posts today! :D

---

### Post by bocmaxima on 2007-02-03
> **meng said:**
> Hey there - did you read my post? I wouldn't blame you if you hadn't, lots of folks seem to be ignoring my posts today! :D

I did read it, but I dont need write access at all, I just need to be able to copy from the NTFS HD to a folder on my desktop. I did it before without ntfs-3g, so why would I need it all of a sudden :(

It wont hurt to try I guess

Although just writing to the NTFS may make things easier

---

### Post by meng on 2007-02-03
Okay, I misunderstood. Funnily enough, I thought that if you wanted to use an NTFS partition to back up your data, it would involve writing to that partition. Obviously what you meant was different from what I interpreted.

What are the ownership and permissions on this folder that you are dragging to?

---

### Post by bocmaxima on 2007-02-03
> **meng said:**
> Okay, I misunderstood. Funnily enough, I thought that if you wanted to use an NTFS partition to back up your data, it would involve writing to that partition. Obviously what you meant was different from what I interpreted.

What are the ownership and permissions on this folder that you are dragging to?

Read and write

---

### Post by amp_man on 2007-02-03
I'll bet only root has access...try using "sudo nautilus" and copying your files through that.

---

### Post by bocmaxima on 2007-02-04
> **amp_man said:**
> I'll bet only root has access...try using "sudo nautilus" and copying your files through that.

Thats what I tried first :(

---

