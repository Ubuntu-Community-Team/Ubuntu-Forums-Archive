---
title: "How do you install yum on Ubuntu 20.04 for LXC ?"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by gstanden on 2020-04-25
Hi,

Yum seems to be gone.  Related to there being no python 2 maybe ?  Not sure.  How does one install yum on Ubuntu 20.04 is the question.  I need it for LXC.

Below I answered this myself (what else is new - that is by far the most common way my posts get answered since nobody seems to ever know or care about the answers to my questions).  Well as George Carlin would say **** '**

So my answer below doesn't really answer WTF happened to "yum" on ubuntu 20.04 because it isn't in the universal repo apparently ??  What I do answer below is how to create RedHat-family LXC containers using LXC 4.0.x on ubuntu 20.x

I STILL NEED TO KNOW HOW TO GET YUM  AND YUM-UTILS INSTALLED OR BUILT FROM SOURCE ON UBUNTU 20.04 FOCAL ...

We're all we Need.

Thanks,

Gilbert

---

### Post by gstanden on 2020-04-25
Ok I've been out of practice for a bit so forgive me ok ?  My wife passed away in March 2020.  She was the most beautiful amazing wonderful person.  The last 18 months she was really sick and required my 24/7/365 care, but more importantly, I required HER 24/7/365 care.  I'm lost without her of course, but I'm back here at the old farmer market stand "Ubuntu" and I cleaned out the wreckage my office had become and it's all neat and tidy and I'M BACK (Stephane and Christian watch out because I'll soon be asking you annoying questions again!)  and I haven't touched Ubuntu since 19.04 nor kept track of anything about the IT world at all.  I loved her with all my heart. 

I did take one poetic license with Alfred, Lord Tennyson, below:  I changed "Arthur" to "Yelena" xxx and "Bedivere" to "Gilbert" and "Lord" to "Lady"

Then loudly cried the bold Sir Gilbert:
"Ah! my Lady Yelena, whither shall I go?
Where shall I hide my forehead and my eyes?
For now I see the true old times are dead,
When every morning brought a noble chance,
And every chance brought out a noble knight.
Such times have been not since the light that led
The holy Elders with the gift of myrrh.
But now the whole ROUND TABLE is dissolved
Which was an image of the mighty world;
And I, the last, go forth companionless,
And the days darken round me, and the years,
Among new men, strange faces, other minds."

         And slowly answer'd Yelena from the barge:
"The old order changeth, yielding place to new,
And God fulfils Himself in many ways,
Lest one good custom should corrupt the world.
Comfort thyself: what comfort is in me?
I have lived my life, and that which I have done
May He within Himself make pure! but thou,
If thou shouldst never see my face again,
Pray for my soul. More things are wrought by prayer
Than this world dreams of. Wherefore, let thy voice
Rise like a fountain for me night and day.
For what are men better than sheep or goats
That nourish a blind life within the brain,
If, knowing God, they lift not hands of prayer
Both for themselves and those who call them friend? 

So now I am back, alone, among the mountains by the winter sea ...

So one does not need yum at all to create RedHat-based distro LXC containers if one uses this method:

orabuntu-services-5.sh:       lxc-create --version
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ **sudo lxc-create -t download -n oracle -- --dist oracle --release 7 --arch amd64**
Setting up the GPG keyring
Downloading the image index
Downloading the rootfs
Downloading the metadata
The image cache is now ready
Unpacking the rootfs

---
You just created a Oracle 7 x86_64 (20200425_07:46) container.
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-destroy -n oracle
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ **sudo lxc-create -t download -n oracle7 -- --dist oracle --release 7 --arch amd64**
Using image from local cache
Unpacking the rootfs

---
You just created a Oracle 7 x86_64 (20200425_07:46) container.
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ **sudo lxc-create -t download -n oracle8 -- --dist oracle --release 8 --arch amd64**
The cached copy has expired, re-downloading...
Setting up the GPG keyring
Downloading the image index
Downloading the rootfs
Downloading the metadata
The image cache is now ready
Unpacking the rootfs

---
You just created a Oracle 8 x86_64 (20200425_07:46) container.
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-ls -f
NAME       STATE   AUTOSTART GROUPS IPV4                      IPV6 UNPRIVILEGED 
afns1      RUNNING 0         -      10.209.53.2, 172.29.108.2 -    false        
afns1-base STOPPED 0         -      -                         -    false        
oracle7    STOPPED 0         -      -                         -    false        
oracle8    STOPPED 0         -      -                         -    false        
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-start -n oracle7
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-ls -f
NAME       STATE   AUTOSTART GROUPS IPV4                      IPV6 UNPRIVILEGED 
afns1      RUNNING 0         -      10.209.53.2, 172.29.108.2 -    false        
afns1-base STOPPED 0         -      -                         -    false        
oracle7    RUNNING 0         -      -                         -    false        
oracle8    STOPPED 0         -      -                         -    false        
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-ls -f
NAME       STATE   AUTOSTART GROUPS IPV4                      IPV6 UNPRIVILEGED 
afns1      RUNNING 0         -      10.209.53.2, 172.29.108.2 -    false        
afns1-base STOPPED 0         -      -                         -    false        
oracle7    RUNNING 0         -      -                         -    false        
oracle8    STOPPED 0         -      -                         -    false        
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-ls -f
NAME       STATE   AUTOSTART GROUPS IPV4                      IPV6 UNPRIVILEGED 
afns1      RUNNING 0         -      10.209.53.2, 172.29.108.2 -    false        
afns1-base STOPPED 0         -      -                         -    false        
oracle7    RUNNING 0         -      10.0.3.223                -    false        
oracle8    STOPPED 0         -      -                         -    false        
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-start -n oracle8
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-ls -f
NAME       STATE   AUTOSTART GROUPS IPV4                      IPV6 UNPRIVILEGED 
afns1      RUNNING 0         -      10.209.53.2, 172.29.108.2 -    false        
afns1-base STOPPED 0         -      -                         -    false        
oracle7    RUNNING 0         -      10.0.3.223                -    false        
oracle8    RUNNING 0         -      -                         -    false        
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-ls -f
NAME       STATE   AUTOSTART GROUPS IPV4                      IPV6 UNPRIVILEGED 
afns1      RUNNING 0         -      10.209.53.2, 172.29.108.2 -    false        
afns1-base STOPPED 0         -      -                         -    false        
oracle7    RUNNING 0         -      10.0.3.223                -    false        
oracle8    RUNNING 0         -      10.0.3.212                -    false        
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ sudo lxc-attach -n oracle8
[root@oracle8 /]# uname -a
Linux oracle8 5.4.0-26-generic #30-Ubuntu SMP Mon Apr 20 16:58:30 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
[root@oracle8 /]# cat /etc/oracle-release 
Oracle Linux Server release 8.1
[root@oracle8 /]# exit
exit
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ 

xxxxxxxxxxxxxxxxxxxxxxxxxx

I had been using this method previously which still does not work, which requires YUM.  Here's what happens if you try to install container the "OLD" LXC way ...

ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ **sudo lxc-create -n oel73c10 -t oracle -- --release=73**
Host is Ubuntu 20.04
Create configuration file /var/lib/lxc/oel73c10/config
Yum installing release 73. for x86_64
failed: Unsupported release 73
lxc-create: oel73c10: lxccontainer.c: create_run_template: 1626 Failed to create container from template
lxc-create: oel73c10: tools/lxc_create.c: main: 319 Failed to create container oel73c10
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ which yum
/usr/bin/yum
ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ yum
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named urlgrabber

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.7.18rc1 (default, Apr  7 2020, 12:05:55) 
[GCC 9.3.0]

If you cannot solve this problem yourself, please go to 
the yum faq at:
  [http://yum.baseurl.org/wiki/Faq](http://yum.baseurl.org/wiki/Faq)
  

ubuntu@ubuntu-ThinkPad-P72:~/Downloads/orabuntu-lxc-6.13.10-beta/orabuntu$ 

So that's it for any other Arthurian knights out there.  Just don't use the old way - use the new syntax for creating containers.

And so it goes ... any additional illumination of WTF is going on here with YUM is most welcome ...

---

