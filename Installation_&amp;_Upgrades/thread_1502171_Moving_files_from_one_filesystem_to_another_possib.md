---
title: "Moving files from one filesystem to another possible?"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by arcelivez on 2010-06-05
Hello,

OK, I have a situation:
1) I would like to backup my files from one partition which is for example xfs(home folder) to a new partition which will be for example ext3, can I just simply copy all the files from xfs partition to the ext3? And will it work all fine? Won't there be any errors or conflicts?

2) And the second thing is, I'm thinking of replanning my partitions this way:

I think that ext3 would be faster than my current xfs filesystem for the home folder, since many apps and other small files are in the home folder, I would then create another xfs partition with folder which i would then mount in the home folder for example the folder videos in home on ext3 would be mounted to the xfs partition, since xfs is faster for larger files? I'm planning on mounting all the stuff like pictures, music, etc on that xfs partition?
Am I any right here? Is it worth? Or is this totally retarded and not worth it? Maybe it would even slow the performance down?

Any suggestions?

P.S.  Please mind that I have mentioned 2 questions in here, which are not completely related :P

Thanks in advance.

---

### Post by tommcd on 2010-06-05
> **arcelivez said:**
> 
1) I would like to backup my files from one partition which is for example xfs(home folder) to a new partition which will be for example ext3, can I just simply copy all the files from xfs partition to the ext3? And will it work all fine? Won't there be any errors or conflicts?
This should not be a problem or cause any data loss afaik. You can always just copy a few files and then check them just to be sure. 

> **arcelivez said:**
> 
I think that ext3 would be faster than my current xfs filesystem for the home folder ...
I would go with ext4, since it is pretty well stable these days and has become the default file system Ubuntu and many, if not most other distros. Even Slackware (which is always very conservative) uses ext4 as the default now.

---

### Post by srs5694 on 2010-06-05
> **arcelivez said:**
> 1) I would like to backup my files from one partition which is for example xfs(home folder) to a new partition which will be for example ext3, can I just simply copy all the files from xfs partition to the ext3? And will it work all fine? Won't there be any errors or conflicts?

It depends on how you do it. For instance, if you use "sudo cp -R", ownership will be changed to root and permissions may not be preserved as you expect. There are many ways to do it that will work, though -- rsync, cp, or tar, for instance, can all do the job, but you may need to use specific options. (The "-a" option to cp, for instance, preserves the most important attributes.) Personally, I use the following for this sort of thing:

```

cd /source/dir
sudo tar cpf - ./ | (cd /dest/dir; sudo tar xvpf -)

```

> 2) And the second thing is, I'm thinking of replanning my partitions this way:

I think that ext3 would be faster than my current xfs filesystem for the home folder, since many apps and other small files are in the home folder, I would then create another xfs partition with folder which i would then mount in the home folder for example the folder videos in home on ext3 would be mounted to the xfs partition, since xfs is faster for larger files? I'm planning on mounting all the stuff like pictures, music, etc on that xfs partition?
Am I any right here? Is it worth? Or is this totally retarded and not worth it? Maybe it would even slow the performance down?

Personally, I wouldn't bother. You'll almost certainly waste more time doing the repartitioning and file-moving than you'd save from any tiny performance benefits of having small user configuration files on ext3fs rather than on XFS. There might be no benefits at all, in fact. This will also restrict your flexibility -- what if you need to store a big file (or several big files) in your home directory but outside of your videos directory, for instance?

---

### Post by tommcd on 2010-06-05
> **srs5694 said:**
> It depends on how you do it. For instance, if you use "sudo cp -R", ownership will be changed to root and permissions may not be preserved as you expect.
Yes it would be better to use rsync with at least the -a option to preserve the existing file permissions.
If the permissions were changed though, you could always just use chown / chmod to reset the permissions to the way you want them.

---

### Post by arcelivez on 2010-06-06
Thanks for the great answers guys. 

So is it possible somehow to use chown for the whole folder tree? I mean for all the files and folder in the folder which owner I am changing? Because right now I just know how to change the owner of the folder, but it doesn't change the owner of it's contents...

---

### Post by tommcd on 2010-06-06
> **arcelivez said:**
> T
So is it possible somehow to use chown for the whole folder tree? I mean for all the files and folder in the folder which owner I am changing? Because right now I just know how to change the owner of the folder, but it doesn't change the owner of it's contents...
If you have a folder ( or directory in geek speak) that you want to change the *ownership* of; and you want the ownership to change *recursively* (in other words, you want the ownership for all sub-directories (sub-folders) to change ownership as well, just use the -R option with chown.
Example:
If I need to change the ownership of my /data directory, as well as all the sub-directories within it, to my user name, I would run:
```
sudo chown -R tom:users /data
```
The -R switch is for recursive. That is, every directory and sub-directory in /data will have it's ownership changed to tom:users as well.
Note that this will place "tom" as the owner, but with the group "users". So anyone in the "users" group could view or possibly modify the data.
If I wanted to chown /data so that only I had access to /data, and no one else on the system could modify the files I would run:
```
sudo chown -R tom:tom /data
```
This way the /data directory would be owned only by me.

You can use chmod to further modify the read, write, and execute permissions if you need to.
DO NOT use chown or chmod on system files unless you have a very good reason to do so, and you really know what you are doing!


Write back if you need more help.

---

### Post by arcelivez on 2010-06-06
Thanks a lot, been wondering how to do that, since there were times I really needed this but I would just have to do the command on every needed directory inside... :D

---

### Post by srs5694 on 2010-06-06
Note that recursively changing the ownership of files after they've been changed (say by improper use of cp -R) may not restore the original ownership. In the case of a home directory, it'll probably be OK; but ownership can vary, and appropriately so, on a file-by-file basis. Similar comments apply to permissions. Thus, it's always best to get it right when doing the copy rather than after the copy is done. In the latter case, you might fix 99% of the problems, but there could be a few problems lurking undiscovered.

---

