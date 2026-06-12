---
title: "Weird missing files on mounted samba share"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by callan79 on 2009-10-03
This one's a bit weird ... I have the following in my /etc/fstab :

```
//192.168.7.2/shared    /media/shared   cifs    auto,nounix,user=me,password=mine,uid=root,gid=bogglers,dir_mode=0770,file_mode=0770
```

(It mounts the shared folder called 'shared' on my NAS. Local filesystem mount point has uid=root and gid=bogglers. This is so that all family members have read/write as they are all in the bogglers group.

This has worked for some time on previous versions of Ubuntu. The share still mounts, and works fine on 9.10 beta.

But when I look at a particular folder, it has less files than the same folder viewed with Ubuntu 9.04, using exactly the same mount command.

In 9.10 beta I'm showing 90 files. Yet in 9.04 I'm showing 120 files. They are all called something.pdf. No weird characters in the filenames. No permissions can even exist, since it's a samba/cifs share.

Will continue to play, just wondering if anyone else has seen the same problem ?

Cheers
Callan

---

### Post by Copernicus1234 on 2009-10-03
Interesting. So 30 of the 120 .pdf files doesnt show up in 9.10?

I did some googling and found only old threads about this, but they may still be helpful for you. Google for "missing files samba", I got a few links that may be relevant to your problem.

---

### Post by callan79 on 2009-10-03
No solution yet, just some updates :

 - The affected folder is called Warranties & Receipts
 - If I rename it without the &, it makes no difference
 - If I copy the folder with a new name, it makes no difference
 - If (on another computer) I copy one of the missing files, with a new name, it does NOT appear on the karmic machine
 - If (on another machine) I create a new file, it appears OK on the karmic machine


On the parent folder I did a count (find * | wc -l) of all files and directories. There is a discrepancy of around 100 items between the karmic machine and a jaunty machine.

Again I'll keep playing!

Interested to see if anyone else has the same problem.

Cheers
CD

---

### Post by hybridr6 on 2009-10-07
> **callan79 said:**
> This one's a bit weird ... I have the following in my /etc/fstab :

```
//192.168.7.2/shared    /media/shared   cifs    auto,nounix,user=me,password=mine,uid=root,gid=bogglers,dir_mode=0770,file_mode=0770
```

(It mounts the shared folder called 'shared' on my NAS. Local filesystem mount point has uid=root and gid=bogglers. This is so that all family members have read/write as they are all in the bogglers group.

This has worked for some time on previous versions of Ubuntu. The share still mounts, and works fine on 9.10 beta.

But when I look at a particular folder, it has less files than the same folder viewed with Ubuntu 9.04, using exactly the same mount command.

In 9.10 beta I'm showing 90 files. Yet in 9.04 I'm showing 120 files. They are all called something.pdf. No weird characters in the filenames. No permissions can even exist, since it's a samba/cifs share.

Will continue to play, just wondering if anyone else has seen the same problem ?

Cheers
Callan

Thanks again for the response in my thread Callan. As for your problem I was having an issue where cifs was issuing the remote owner locally, and this would allow me to create files/folders, but not modify them. Along with a host of other permission issues. I'm not sure this is what you're experiencing but maybe this explanation from the Ubuntu Docs will help.

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

> CIFS remote ownership enforcement

When you connect using CIFS to a server which supports Unix permissions (e.g. Samba), CIFS will by default try to enforce remote Unix ownership UIDs and Unix permissions when you try to access the share. i.e. if a file is owned by UID 502 on the remote server, then the local kernel will try to enforce the same permissions if it were owned by UID 502 on the local machine. Note: This has nothing to do with the remote server's security settings. This is an extra local ownership enforcement by the filesystem driver. It is a feature to allow use of remote share as a local drive with full Unix permissions enforcement if users match.

But if this is a public share, then chances are, the remote UIDs will not make sense locally. A remote UID might be a completely different user or might not exist at all on the local machine. If remote UIDs and local UIDs do not match, then local users will have trouble using the share. To disable this, use the "noperm" mount option. Remote permissions and UIDs will still be visible, but they will not be enforced locally. 

Good Luck,
hybridr6

---

### Post by callan79 on 2009-10-08
> **callan79 said:**
> No solution yet, just some updates


Okay just to note this for the record .... in case anyone else has a similar issue.

I changed my fstab to this :

```
//192.168.7.2/shared	/media/shared	cifs	noauto,noperm,user=xxx,pass=xxx,gid=mygroup,dir_mode=0770,file_mode=0770
```

Now, the dir_mode and file_mode don't seem to do anything - this only seems to have an effect when the 'nounix' option is used.

If I DO NOT use 'nounix' then I can see all my files. If I put 
'nounix' in, suddenly those 30 files go missing again.

Without the nounix, I am able to see the real owners and permissions of the files. I'll check it out tomorrow and work out what the story is!

CD

---

### Post by agds on 2009-10-15
Did you figure out what was going on?  I'm experiencing something similar when mounting a Samba share from Ubuntu 8.04 on a Windows 7 box.  In my case, it's MP3 files that are invisible on the share.  But it's only some of them.  I haven't found a rhyme or reason to it.

---

### Post by callan79 on 2009-10-15
> **agds said:**
> Did you figure out what was going on?  I'm experiencing something similar when mounting a Samba share from Ubuntu 8.04 on a Windows 7 box.  In my case, it's MP3 files that are invisible on the share.  But it's only some of them.  I haven't found a rhyme or reason to it.

Hi agds,

No, I haven't found a reason, I was actually thinking of lodging a bug report. It happens the same in 9.10 64-bit and 32-bit (I tested that last night).

If I remove the 'nounix' option from my mount command, I get all files showing up, and some of them have different owners and groups.

But with the 'nounix' enabled, some files vanish - but there is no pattern. The missing files are NOT simply all files of a certain owner, or size, or date, or permission. It's somehow random.

I looked ay music folder last night - 112 items, where there should be more like 2000 items.

Will continue playing and report back ASAP.

Cheers
Callan

---

