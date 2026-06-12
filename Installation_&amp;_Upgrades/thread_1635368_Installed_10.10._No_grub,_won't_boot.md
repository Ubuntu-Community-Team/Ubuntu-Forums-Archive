---
title: "Installed 10.10. No grub, won't boot"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by drazelian on 2010-12-01
Today I completely formatted my hardrive (laptop), and partitioned it up.
I made 200 gigs for win 7 (ntfs)
25 gigs for ubuntu
and 3 gigs for swap space

First I installed windows 7 on the 200 gig partition. Once that was done
I booted into ubuntu live, and began the install. I gave ubuntu the 25 gig partition, as an ext2 filesystem, and / as a mount point.
I made the 3 gig partition's file system linux swap.

After the install was done, It told me to restart the computer, which I did.

It did not boot into grub, it just went into windows 7 as it normally would, as if ubuntu had never been installed in the first place.

What can I do to make my PC recognize ubuntu's presence and make it so I can get to grub and choose my OS?
Thanks

---

### Post by drazelian on 2010-12-01
bump

---

### Post by oldfred on 2010-12-01
The last part of the install should have put grub into the MBR of sda. 

So we can see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by drazelian on 2010-12-01
I should have this up in a few hours

---

### Post by drazelian on 2010-12-02
I can't navigate in the terminal to where I have the script, so I'm unable to execute it.
This is what happens when I simply navigate to the desktop, if I add the code to execute the script, the same thing happens
```
ubuntu@ubuntu:~$ cd ~/desktop
bash: cd: /home/ubuntu/desktop: No such file or directory

```

I am booting off live CD

Past ubuntu installations done the exact same way have worked for me. I don't understand why 10.10 won't.

---

### Post by Quackers on 2010-12-02
Go to where you downloaded the bootscript to (probably Downloads) and copy the file and then paste it on the Desktop, then run the command

---

### Post by drazelian on 2010-12-04
While partitioning, I messed up pretty bad somehow, and lost everything on my hard drive. Although that was a pretty big loss, it allowed me to do what I wanted to do. I put all my partitions back into 1 siingle one. First I installed Win7, then I installed ubuntu side by side with it, and it worked great. Thanks for the support.

---

### Post by Habeouscorpus on 2010-12-04
Linux is Case-Sensitive. So it sees

/home/ubuntu/desktop

and 

/home/ubuntu/Desktop

differently. Try capitalizing this time. (This is the mistake I make nearly every day...)

---

