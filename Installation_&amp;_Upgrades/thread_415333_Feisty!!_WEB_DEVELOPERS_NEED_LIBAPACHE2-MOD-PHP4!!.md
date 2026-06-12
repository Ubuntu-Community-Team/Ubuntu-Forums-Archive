---
title: "Feisty?!?! WEB DEVELOPERS NEED LIBAPACHE2-MOD-PHP4!!!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by kimu on 2007-04-20
libapahce2-mod-php4 is part of the repository, but there is no package to download.

WEB DEVELOPERS NEED IT!!!!

I've read that libapache2-mod-php4 should not be more part of the repository. ARE YOU JOCKING???? 

Who use ubuntu for web developing absolutely need it. Put it back in the repository, pls.

---

### Post by hardyn on 2007-04-20
developers do not check here, please post @ launchpad.

---

### Post by maxamillion on 2007-04-20
> **kimu said:**
> libapahce2-mod-php4 is part of the repository, but there is no package to download.

WEB DEVELOPERS NEED IT!!!!

I've read that libapache2-mod-php4 should not be more part of the repository. ARE YOU JOCKING???? 

Who use ubuntu for web developing absolutely need it. Put it back in the repository, pls.

It has simply been replaced by php5 ... [http://packages.ubuntu.com/feisty/web/libapache2-mod-php5](http://packages.ubuntu.com/feisty/web/libapache2-mod-php5)

---

### Post by kimu on 2007-04-21
> **maxamillion said:**
> It has simply been replaced by php5 ... [http://packages.ubuntu.com/feisty/web/libapache2-mod-php5](http://packages.ubuntu.com/feisty/web/libapache2-mod-php5)

it hasn't been replaced. libapache2-mod-php5 and libapache2-mod-php4 have always been in the repository both. It was people choice or need to install version 4 or 5. Now Ubuntus' team decide for us.
For me it means that if my projects don't work well with php5 I have to format my pc and reinstall edgy or dapper, only for a package, wasting a lot of time.

Funny....:mad:

---

### Post by DJ_Peng on 2007-04-21
I got bitten by this bad decision myself. I need to test soaftware written in PHP4, and PHP5 does me no good. Pleas eadd PHP4 back into the repos for Feisty.

---

### Post by K.Mandla on 2007-04-22
[quote=Martin Pitt]we have not supported PHP 4 for three releases now, and it's time to remove it from the archive to avoid shipping unsupported stuff with known security vulnerabilities. The world has mostly moved to PHP 5 anyway.[/quote]

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-February/023296.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-February/023296.html)

---

### Post by Bat on 2007-05-10
> The world has mostly moved to PHP 5 anyway.

That's got to be the stupidest thing I've read today.  Who *is* this guy, and what world is he talking about?  PHP 5 failed where it mattered most: with commercial web hosts.  As a result, most web hosts support only PHP 4, and if they have plans to upgrade to PHP 5 it's always with a one-two year lead time, even now with PHP 6 on the horizon.

Whatever world this Martin guy lives on, it must be nicer than here.  Sadly, I can't seem to get tickets on the Space Shuttle.  Perhaps Mark Shuttleworth can help?

---

### Post by ametade on 2007-05-21
I'm using eZ Publish as CMS for my clients ([http://ez.no](http://ez.no)). EZ Publish requires PHP 4 (It simply doesn't work on PHP 5).

On my servers I'm using Dapper but PHP4 doesn't seams to get any security updates. Do I have to change to Debian? I thinks this is a very bad move to Ubuntu on the server platform.

---

### Post by siteguru on 2007-05-21
[Any use?]("http://jdv.hopto.org/index.php?/archives/84-Ubuntu-Feisty-with-Apache-2.2,-PHP4-with-FastCGI-and-MySQL-support.html")

---

### Post by Peter Mount on 2007-05-24
> **siteguru said:**
> [Any use?]("http://jdv.hopto.org/index.php?/archives/84-Ubuntu-Feisty-with-Apache-2.2,-PHP4-with-FastCGI-and-MySQL-support.html")

It doesn't seem to say how to get it to work with MySQL 4.x, which is what my web host uses together with PHP4.x.

I'm actually thinking of switching back to Fedora because of this issue. Ironically I changed to Kubuntu from Fedora originally because it was easy to install PHP4 with MySQL4 on it. Now I've found instructions on doing the same in Fedora [here]("http://www.transcendingthought.com/content/view/31/42/") and it's supposed to work with any version of Fedora.

It will cost my clients more money in hosting fees if I change to a different web host that has PHP5 etc. So I simply must be able to test things in PHP4 and MySQL 4. 

I now have an extra hard drive and I have FC6 on CDs so I can try it on that. I love using Kubuntu but if I'm unable to use PHP4 and MySQL 4 on it then I might be forced to give up on it.

---

### Post by toppy on 2007-06-01
I think it was a mistake not to include PHP4 in Feisty.  I recently purchased a new dev box, installed Feisty and got ready to do some coding.  Obviously I was a bit suprised and put out by this decision.  I was planning on heading back to Dapper but then I read the following thread:

[http://ubuntuforums.org/showthread.php?t=385052&highlight=php4](http://ubuntuforums.org/showthread.php?t=385052&highlight=php4)

Reading Fujitsu's posts didn't sit well with me.  I kept getting flashes of Microsoft in my mind as I read the responses.  The lack of consideration about this situation and the potential loss of time and money (recoding several apps, switching servers, learning the changes, etc) for being forced to switch over wasn't even a consideration.  

Considering that and that this new computer would be my main system I tried Freespire.  It does have some relations to Ubuntu and if they decide to remove PHP4 any time soon I'll be finding something else.

---

### Post by pestilence on 2007-06-02
I am a Linux users for many years, I was suprised after turning from gentoo recently to Kubuntu just to realize that php4 support was removed. It is no hassle for me to compile it, but I would prefer to have it inside the native package management system of Kubuntu.
Developers believe that PHP4 is obsolete, but I strongly disagree, there is still a huge community of developers that do use PHP4 either because they still don't want to migrate to PHP5 or because they can't due to server restrictions (I work as a freelancer and many of the hosting companies I had the chance to work with do NOT yet support PHP5).
PHP5 allthough backwards compatible is different from PHP4 and will create problems, objects passed by reference and not copyed (as in PHP4) would require many hours of searching inside major PHP4 projects (as frameworks)...just imagine having to search a few thousand lines of code for "=" and replacing to "=&" just for a simple "difference" between PHP4 and PHP5.
PHP4 should be yet available to Kubuntu users, since PHP has not declared PHP4 as obsolete I see no reason for stopping support of it.

---

