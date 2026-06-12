---
title: "how apt-get command works?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by ycp1 on 2010-08-10
I am trying to understanding package tools in ubuntu. After I read some documents on internet. I did some exercise myself. And I got some questions. I installed fex package.

```
# aptitude install fex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  fex libdigest-md5-file-perl{a} xinetd{a} 
The following packages will be REMOVED:
  inetutils-inetd{a} 
0 packages upgraded, 3 newly installed, 1 to remove and 4 not upgraded.
Need to get 306kB of archives. After unpacking 709kB will be used.
Do you want to continue? [Y/n/?] .
.
.
```

It installed 3 packages and removed 1 package. And I remove fex package.

```
# apt-get remove fex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdigest-md5-file-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fex
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 463kB disk space will be freed.
Do you want to continue [Y/n]?
.
.
```

My understanding is that there are two unnecessary packages left. Those are libdigest-md5-file-perl and xinetd. And I thought that lost inetutils-inetd package. But I didn't.

```
# dpkg --get-selections | grep inetutils
inetutils-inetd					deinstall
# dpkg --get-selections | grep xinetd
xinetd
```

So, I tried to remove not removed packages. They are libdigest-md5-file-perl and xinetd.

```
# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdigest-md5-file-perl
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? 
```

My first question is why this command doesn't remove xinetd package? And another question is apt-get command reinstall inetutils-inetd package when I ran "apt-get remove fex"? Thank  you for your helps.

---

### Post by dabl on 2010-08-10
Do not assume (like I once did), that apt-get and aptitude are functionally the same thing -- they are not. If you're going to use aptitude, then that's fine, but note:

[http://blogs.koolwal.net/2009/02/20/howto-switching-from-apt-get-to-aptitude/](http://blogs.koolwal.net/2009/02/20/howto-switching-from-apt-get-to-aptitude/)

[http://www.andrewault.net/2010/05/03/aptitude-vs-apt-get-comparison-2/](http://www.andrewault.net/2010/05/03/aptitude-vs-apt-get-comparison-2/)

You can also find some minor flame wars on the topic:

[http://forums.debian.net/viewtopic.php?f=17&t=34499](http://forums.debian.net/viewtopic.php?f=17&t=34499)

---

### Post by ycp1 on 2010-08-11
Thank you for your reply. I made a mistake that I used aptitude command while I was exercising to understand apt-get command. Now, I try these two commands, 

```
# apt-get install fex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdigest-md5-file-perl
The following NEW packages will be installed:
  fex libdigest-md5-file-perl
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 154kB of archives.
After this operation, 537kB of additional disk space will be used.
Do you want to continue [Y/n]?  n
Abort.
# aptitude install fex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  fex libdigest-md5-file-perl{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 154kB of archives. After unpacking 537kB will be used.
Do you want to continue? [Y/n/?]
```

Both gave me same results in this time. My understanding is that the very first aptitude install fex command removed inetutils-inetd package because it is not used anymore in my system. Or, because inetutils-inetd package must be removed to install fex package. Which one is correct?

In the last case, is it okay to remove packages to install a package?

I also ready posts in your suggests. Thank you. Now, I know that I must not use apt-get and aptitude interchangeably. I also found out that aptitude command can replace apt-cache command. A great thing I now know how easy to put a package into hold state from upgrade using aptitude. One thing I still didn't find is how I can get a list of installed packages using aptitude instead of dpkg. Great thanks for you, dabl.

---

### Post by dabl on 2010-08-11
I'm an apt-get user, because aptitude is not good to use on Debian Sid, and I run sidux as well as Kubuntu.  So, I am not skilled with aptitude.  If you study ```
man aptitude
```, you should be able to learn how to output your list of installed packages (assuming that is something aptitude can do).

---

### Post by ycp1 on 2010-08-11
Thank you for your reply, dabl. Please, forget things about apt-get command that I used above.
  My question is about when "aptitude install anewpackage" command will remove another package? I saw it happened bofore. Is it because the packages are not necessary in my system? If it is not the case, then is it because the packages must to be removed to install a new package? That is my first question and there is nothing to deal with apt-get command.

Let's suppose that aptitude remove packages to install a new package, shouldn't I worry about the removed packages? This is my second question.

I already read many part of aptitude and apt-get manpages before pose here. I also read some about debian package tools. But I couldn't get clear understanding about these questions. Do you know the answers for me?

---

### Post by ycp1 on 2010-08-13
I found some of answer myself from [-how-to-get-a-list-of-all-installed-packages-458119/"]LinuxQuestions.org]("http://www.linuxquestions.org/questions/debian-26/[aptitude). I also found [aptitude manual page]("http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/index.html"). There is [references]("http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html") in the web page.

```
$ aptitude search ~T      #shows all packages
$ aptitude search ~i      #shows all installed packages.
```

I hope to find other answers later.

---

### Post by ycp1 on 2010-08-21
I am closing this thread. I realized how hard to understand inside of package tools to answer all my questions. It would take longer than I thought. But I found where to start. Someone who had same issue like me will find helps from these two links

[http://www.linuxquestions.org/questions/linux-general-1/understanding-debian-package-tools-826059/](http://www.linuxquestions.org/questions/linux-general-1/understanding-debian-package-tools-826059/)
[http://www.linuxquestions.org/questions/blog/craigevil-176422/grokking-debian-gnu-linux-3073/](http://www.linuxquestions.org/questions/blog/craigevil-176422/grokking-debian-gnu-linux-3073/)

PS> I realized that general questions about linux system can be easily found in [www.linuxquestions.org]("http://www.linuxquestions.org"). This forum is good for Ubuntu questions.

---

