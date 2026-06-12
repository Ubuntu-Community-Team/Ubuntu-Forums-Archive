---
title: "Anjuta 1.2.4 on Edgy?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by daniloeu on 2006-10-29
Hi guys!

I have a question.
I think that everybody know that anjuta2.0.2 is a alpha version (a lot, lot looot of bugs), but it is on official edgy repository.
The question is: How can I install anjuta1.2.4 (stable, exist on drapper) on Edgy without need to compile it from source?

Thanks for all!

[]'s

Danilo Cesar

---

### Post by Tiede on 2006-11-03
I ditto and would like to know if it is advisable that I ```
sudo apt-get remove --purge anjuta anjuta-common
``` and then download the 1.2.4 version from the dapper repos... Will it break? (I' thinking it may send me to dependencies hell)...

---

### Post by daniloeu on 2006-11-03
[COLOR="Red"]FORGET THIS STEPS!!! ITS NOT SO GOOD...
READ THIS POST FOR A EASY SOLUTION...
[http://ubuntuforums.org/showthread.php?p=1686380#post1725030](http://ubuntuforums.org/showthread.php?p=1686380#post1725030)[/COLOR]

In really, its will not work, because libvte4 in not installable on Edgy. (and Anjuta1.2.4 depend of this package)

BUT, if we follow some steps it will works.

First download anjuta1.2.4 and anjuta-common from Dapper sources
Then edit anjuta1.2.4 depends, and replace libvte4 to libvte9

Install anjuta packages with dpkg -i

After that, exec this command:

sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

Now anjuta1.2.4 will work with no problem on Edgy...



***************************************************

To make this process more easy, I had made a meta package "anjutaM" that is anjuta1.2.4 with modifications on deb depends. But it's conflict with anjuta. 
Why?
It will be more easy to install/control this packages on Edgy's updates. If you want to install anjuta again, anjutam will be automatically removed.

Download this package on [http://www.danilocesar.com/blog/wp-content/uploads/2006/11/anjutatar.gz]("http://www.danilocesar.com/blog/wp-content/uploads/2006/11/anjutatar.gz")

Do not forget to create lib link, or it will do not work well..

If someone have any doubts, talk to me!

[]'s

Danilo Cesar
[http://www.danilocesar.com](http://www.danilocesar.com)

---

### Post by muxecoid on 2006-11-06
OK, the original way breaks the dependencies, I'll try your variant later.

2.0.2 is unstable alpha, why did Ubuntu maintainers replace 1.24? Didn't they see the notice on the official site, that 2.0.2 is alpha? Didn't they care about the stability?

I suggest petition asking to add old Anjuta (as anjuta1, anjutam or whatever) to the official repositories with libvte problem solved as well?

---

### Post by daniloeu on 2006-11-06
Hello!

Some days ago I talk with Rob Branford (maintainer of anjuta on debian), and he tell me that anjuta 2.0.2 is a problem on debian too, and its reverted now.

I think that Ubuntu MCU will not revert it soon, so I did that myself.

I describe some steps to do it on my blog (Portuguese only, sorry)
[http://www.danilocesar.com/blog/2006/11/03/anjuta-124-e-ubuntu-edgy-sim-e-possivel/](http://www.danilocesar.com/blog/2006/11/03/anjuta-124-e-ubuntu-edgy-sim-e-possivel/)

But, if you dont want to read, add this line on your /etc/apt/source.list
deb [http://www.danilocesar.com/ubuntu](http://www.danilocesar.com/ubuntu) debs/

And 

```

apt-get update
apt-get install anjuta1.2.4

```

I have Skype (last version), anjuta1.2.4 and gliper 0.89 on my repository.

---

### Post by muxecoid on 2006-11-06
Thanks. I hope I can trust it.;) Any digital signatures?

[joke]Don't tell people that you have Skype, they'll ask questions about your repository orally.[/joke]

---

### Post by daniloeu on 2006-11-06
Hi...

Yes, you can trust on it... (I instaling from there)

About signatures.. well.. I learn how to edit deb files today...
I'm reading some debian's tutorials now, And I will try to make it...
Apt-get is showing some warnings with anjuta1.2.4. Don't worry about that, Its a packing problem and I'm fixing it, but it's do not cause any problem.

[joke]Don't tell people that you have Skype, they'll ask questions about your repository orally.[/joke] LOL  \0/

---

### Post by daniloeu on 2006-11-06
Hi Everybody!

I have the pleasure to say that all the problems with packing had been fixed. Now you can install anjuta1.2.4 without any problem with Ubuntu Edgy!

```

echo "deb http://www.danilocesar.com/ubuntu debs/" >> /etc/apt/sources.list
apt-get update
apt-get install anjuta1.2.4
```

Any problem, please tell me:
danilocesar [on] danilocesar [dot] com

---

### Post by mdurham on 2006-11-29
> **daniloeu said:**
> Hi Everybody!

I have the pleasure to say that all the problems with packing had been fixed. Now you can install anjuta1.2.4 without any problem with Ubuntu Edgy!

```

echo "deb http://www.danilocesar.com/ubuntu debs/" >> /etc/apt/sources.list
apt-get update
apt-get install anjuta1.2.4
```

Any problem, please tell me:
danilocesar [on] danilocesar [dot] com

Thanks for your help daniloeu, I now have a working IDE again.
Mike

---

### Post by Duwi on 2006-12-01
thanks daniloeu,

it worked just perfect.

thanks for your help and work

---

### Post by surfingpenguin on 2007-03-04
Hey, I'm trying to downgrade to anjuta1.2.4, but when i follow your instructions, it seems that there is no anjuta1.2.4 package, only a anjuta1.2.4-common. this is the output of the install:

alejandro@walt:/usr/lib$ sudo apt-get install anjuta1.2.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package anjuta1.2.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  anjuta1.2.4-common
E: Package anjuta1.2.4 has no installation candidate

Help please? I need to get anjuta working fairly soon. thanks

---

### Post by surfingpenguin on 2007-03-04
Okay, nevermind. I found the problem. The package you have is ix86, and im on a PPC machine. Oh well, looks like im going to have to compile  the source code myself then. Thanks anyways.

---

### Post by daniloeu on 2007-03-04
No!

You Don't need to do that...

You can download .deb package from debian's original sources, and change some package headers, removing libvte depend's. Than you need to create a symbolic link to the last version of libvte... and it's done.

---

### Post by surfingpenguin on 2007-03-05
Ah. I made my own .deb file by editting one i downloaded from the debian repositories, but I didn't realize the symbolic link stuff and got a libvte error when I ran anjuta. I went ahead and compiled from source and got it working just fine.

Thanks a lot anyways.
I really need an x86 laptop...

---

### Post by wuziq on 2007-03-13
> **daniloeu said:**
> Hi Everybody!

I have the pleasure to say that all the problems with packing had been fixed. Now you can install anjuta1.2.4 without any problem with Ubuntu Edgy!

```

echo "deb http://www.danilocesar.com/ubuntu debs/" >> /etc/apt/sources.list
apt-get update
apt-get install anjuta1.2.4
```

Any problem, please tell me:
danilocesar [on] danilocesar [dot] com

THANK YOU!  you rock!   :guitar:    :P

---

### Post by chinmaykamat on 2007-03-29
Thanks a lot mate....works without any problem:)

---

### Post by obleak on 2007-04-04
Does anyone know whats going to happen in a fiesty upgrade (which currently has anjuta 1.2.4a in the repos)?

ie 
will edgy official anjuta downgrade to 1.2.4a? - (issue - the projects I started in 2.0.2 needed major work to compile in 1.2.4)
will daniloeu's anjuta switch to fiesty's?
or will it need manual intervention?

Must say I'm surprised ubuntu only put the unstable version of anjuta in edgy.
Although I'm all for bleeding edge technology it would have been cool to have both the stable and unstable versions in the repo's and let the users decide which they want...

---

### Post by surfingpenguin on 2007-04-05
I'm running feisty now, and they downgraded to 1.2.4. I think you can opt for 2.0.2, but I didn't bother trying.

---

### Post by daniloeu on 2007-05-29
On Feisty repository you can download anjuta1.2.4. Its the Oficial Version there.

But (thanks Naba) you can download the 2.1.X from Anjuta repository. I using it and I dont find any bugs yet.
Follow this link: [http://ubuntuforums.org/showthread.php?t=441113](http://ubuntuforums.org/showthread.php?t=441113)

And no, I will not change anything on my repository. You can still trusting on it. =)

[]'s

Danilo Cesar
[http://www.danilocesar.com](http://www.danilocesar.com)

---

### Post by mr.kuhi on 2007-11-20
thenks m8, you save my life!

---

