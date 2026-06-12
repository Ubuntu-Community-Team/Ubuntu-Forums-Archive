---
title: "better installing mechanisms"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2010-10-26
Hi all,

My question regards installing software on Ubuntu.

1. Is there possibly anyway which I can install software without having to depend on the repository? Some of us, especially those found in poorer countries, don't have internet connections, at least their inconvenient if you don't own a laptop, which is pretty much a luxury; broadband can be a dream or too expensive. I know about packages.ubuntu.com but the procedure seems a bit cumbersome, and definitely wouldn't attract new users who don't have a convenient internet connection. If there is a better way, please inform me.

2. What if I download .tar.gz files and install them on Ubuntu? Are they that different from the packages that come through the repository?

3. Can anyone point me where I can raise and perhaps discuss more effectively about this problem; the lack of suitable internet connection especially in poorer countries and the inconvenience it carries along with it when it comes to installing software freely without any hassle? I really want Canonical to take this issue into consideration. You would find independent software for Windows here and there (at least easily searchable on the net whenever available) which, for users that don't have internet, could be a little difficult for them to quit Windows and go to Ubuntu.

Thanks

---

### Post by EthioJOB on 2010-12-20
Hi,

I've been waiting for someone to give a suggestion but so far none. Can somebody *please* address my questions? I'd really appreciate it. :D

---

### Post by sikander3786 on 2010-12-20
Welcome to the forums :-)

And sorry that your Question wasn't addressed in such a long period.

For offline package installations, Keryxproject is the best solution. You can use anyother Windows/Linux PC with Internet access to download the packages and then install them on your intended Ubuntu ;-)

[http://keryxproject.org](http://keryxproject.org)

Some other options here.

[https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

---

### Post by EthioJOB on 2010-12-22
Thanks [sikander3786]("http://ubuntuforums.org/member.php?u=806649")! Your suggestions look very good and really helpful. I'll look into them. 

If you can help me once more, I'be been wondering about the difference between tar.gz, tar.bz, etc and .deb files. I know that the former file types will need to be compiled, which I don't mind taking time to learn. What I really want to know is if there is any difference between them. I mean, which would be better; is .deb's advantage is that its only readily compiled, or are there other differences as well? What would be the advantage or disadvantage if I compile and install the .tar.gz, etc files (cuz they seem to be easy to locate on the net, and I've heard that they're more updated)?

---

### Post by gadolinio on 2010-12-22
> **EthioJOB said:**
> Thanks [sikander3786]("http://ubuntuforums.org/member.php?u=806649")! Your suggestions look very good and really helpful. I'll look into them. 

If you can help me once more, I'be been wondering about the difference between tar.gz, tar.bz, etc and .deb files. I know that the former file types will need to be compiled, which I don't mind taking time to learn. What I really want to know is if there is any difference between them. I mean, which would be better; is .deb's advantage is that its only readily compiled, or are there other differences as well? What would be the advantage or disadvantage if I compile and install the .tar.gz, etc files (cuz they seem to be easy to locate on the net, and I've heard that they're more updated)?

Hi. The main difference is the fact that .deb files are already compiled and ready to install, just by double-clicking them. Other differences come from this one. For example, .deb files are not available sometimes, because they require someone to do that compiling job and spread it, and that might take some months to happen. Also, debs tend to be older versions for this same reason; newer versions are more rapidly uploaded as source code (which is what you get in packages as .tar.gz or other formats like .tar.bz2 and .tar). Installing debs is also a neat way of dealing with this task: they often put the application in the main menu under the corresponding group (office, games, system, etc.) automatically, and foresee an easy way to uninstall it in the future (if you compile source code, you have to make sure to do it yourself).

The main problem I've found with source code is that you often need to deal manually with missing dependencies. The deb looks for any other piece of software that the application needs, if that's the case (it uses the repositories). But if you want to compile source code you might find that other pieces of software are needed (dependencies), and you need to find out what is it that you need to install first, find it, install it, then try to continue with the source code... and find out that you also need more dependencies.

In conclusion, the main difference is that debs are far easier to use, but harder to find. But once the application is installed, it works the same way.

I'd recommend you this website: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Hope you find this useful. Reply if you have any further doubts.

---

### Post by EthioJOB on 2010-12-22
Thanks, gadolinio. Actually, you gave me a pretty good idea. Difficulty of finding debs is the reason I posted the question in the first place.

I don't mind learning and seeing the compiling process through. Regarding the dependencies, won't Synaptic be able to give a hint of the required dependencies (by selecting the corresponding deb package and viewing the dependencies it may list)? Won't these dependencies work for tar files compiled into debs? (Of course, finding these dependencies themselves, if they work, may be difficult, though I may use sikander3786's suggestion)

---

### Post by sikander3786 on 2010-12-22
Yes Synaptic would give you an exact idea of the depencdecies. Once you mark a packages for installation in Synaptic, it would pop up a Dioalog Box listing the dependencies. And that can be exported to a script. Follow the 2nd link in my above post.

Regarding compilation, there is nothing bad except that you won't receive any updates automatically.

Keryx is the best solution. It always downloads all the needed dependencies once you create a new project from your Ubuntu installation. And in addition, it can download all the updates and then, they can be installed offline to your Ubuntu PC.

I would strongly recommend to try Keryx at least once instead of wandering here and there.

---

### Post by EthioJOB on 2010-12-23
Keryx strongly preferred, noted.

Would these suggestions would work for Ubuntu system updates as well? I believe this is an important factor.

---

### Post by sikander3786 on 2010-12-23
> 
Would these suggestions would work for Ubuntu system updates as well?

Yes they would. Actually this is what the keryxproject.org title says ;-)

> Keryx Project | Updates for offline Linux users

---

### Post by EthioJOB on 2010-12-24
Thanks a lot guys. Love this forum!!

---

### Post by gadolinio on 2010-12-26
> **EthioJOB said:**
> Thanks a lot guys. Love this forum!!
Here's a link to a site where you can find debs.
[http://linuxappfinder.com/](http://linuxappfinder.com/)

---

### Post by EthioJOB on 2011-02-01
Hi guys, I'm back.

Keryx 0.92 seemed a little easier to use. I have now Ubuntu 10.10 installed, and you can use only Keryx 1.0, the installable version. Somehow I find it a bit confusing. 


[LIST=1]
[*]I've added the name of my computer in Keryx
[*]The next step seems to copy the profile and take it to the online PC. I take it its the folder with my PC's name on it, though I'm not sure.
[*]I'm a little lost on how to download an updated repo or any software I want. Do I use Keryx 0.92, 1.0, do I need to bring the copied folder along, etc. A little clarification here would be appreciated.
[/LIST]
Please do tell me what I'm missing here or what I need to do next step by step.

---

