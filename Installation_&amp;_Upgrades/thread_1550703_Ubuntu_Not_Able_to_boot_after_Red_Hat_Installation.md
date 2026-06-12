---
title: "Ubuntu Not Able to boot after Red Hat Installation"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by anirudhtomer on 2010-08-11
[IMG]http://localhost/rss/file.jpg[/IMG]


Hello Guys I installed Red Hat Enterprise Linux 5.1 on my machine.

I made a primary partition of 15 GB for it & set the mount point as "/"
& then I gave 4GB to swap space.

once the Red Hat was installed successfully I tested it. It was running nicely.

then I installed Ubuntu 8.10 on my machine. I gave it another 15 GB (different then that of RED Hat)  of my hard disk
& set the mount point as "/".

It then installed ubuntu successfully.

now since the MBR was overwritten by ubuntu's GRUB ububtu's loader appeared instead of that red hat's boot loader.

now when I try to boot ubuntu some error comes up whose SCREENSHOT i have paste above.

I tried to search on some sites which told how to have dual linux on a machine but I was not able to get the thing completely. I mean like how they set the mount point as /home; which distribution to be installed with mount point "/" & which one with "/home"
It got messy for me.

please help me out. I can think of what is happening there...like Red hat might have set some permissions on that root partition because of which ubuntu is not able to access it but I don't know how to get it right.

Even a few days earlier I tried to Install ubuntu first & then Red Hat but that time red hat gave error (mount point not available) while setting the mount point as "/"...since while installing ubuntu I had given mount point as "/" as well.

Thanks in advance.

---

### Post by snowpine on 2010-08-11
Hello, I can't see your screenshot with the error message so I can't help specifically, can you post the error message as text in a posting?

While we're waiting for that, I just wanted to point out that both Red Hat 5.1 and Ubuntu 8.10 are completely and entirely obsolete and unsupported. The current Red Hat Enterprise Linux 5.5 is available from [http://redhat.com](http://redhat.com) and the current Ubuntu 10.04 from [http://ubuntu.com](http://ubuntu.com)

The current Ubuntu release uses GRUB2 rather than the obsolete "legacy" GRUB, and that difference right there might solve your problem.

---

### Post by oldefoxx on 2010-08-11
You can mix distros by putting them on different partitions, but you must prevent /home from being shared among them.  /Home holds all user accounts except root, and hold specific user account configuration settings that are not universal in hature and impact each installed distro differently.

With Ubuntu, you can designate a specific partition to hold /home, but that just means each install requres a companion partition to hold / and the other folders, because the installer lets each partition be designated for only one purpose.  Make it /, and it will include what is not assigned elsewhere except for /home, because if there is an existing /home somewhere, the installer grabs that instead.  This might please some, but it is inherantly a bad idea.

There are at least two methods of circumventing this.  One is to hide any partitions with /home on the temporarily while doing the install.  This ought to work, but I've not tried it.  Use gparted to work with drives and partitions.  The other is to temporarily rename all the /home folders to something else.  Not super easy, since there is no rename command in Linux,
but mkdir and mv used in sesquence can make it happen.  Getting it back as it was later is more prone to errors, but use care and you can manage it.

The thing is, you can mess things up so bad that you have to completely start over, so understand what you are doing and why, then watch out for possible typos.  You will learn to hate the fact that path statements have to be so long and so exact.  Copy and paste can help, as well as the upper cursor key that lets you back up to previous keyboard entries which you can modify and use again.

That is the general idea.  More specific instruction steps have been laid out in other posts here, to which I have contributed a number.  Unfortunately, many people seem unable or unwilling to read anything that is more than roughly 1.5 lines long with no more than two syllables per word, and no more than three of those, and four or fewer words would be best.  Now if this includes you, you may have a bit of a problem. IMHO UCDI IURT.  See ho much easier it is if said that way? LOL

---

### Post by oldfred on 2010-08-11
If you are going to have multiple installs you need to run this for yourself to document what is where. I run it before and after every system change.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

