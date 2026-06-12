---
title: "How does it work - install software"
date: 2021-05-27
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-05-27
This is a question of curiosity . 
Software vendor  produces an application . 
Software vendor makes the application available for download. 
( In real world this gets pretty complicated...)

Now SAME application can be "installed"  from Ubuntu 
and that process is utterly simple, and in one specific case 
better that "download" from the vendor. . 

Now the question is 

how does Ubuntu "team" manages to 
get the application and "make" it installable  ?

In my opinion there is a difference between 
download 
and
install.

---

### Post by grahammechanical on 2021-05-27
I am completely ignorant of this subject. I imagine that it is not execssively difficult to make a file available for download. The person downloading the file would need a program that fetches the data in the file, error checks that the data being downloaded is complete and at the same time stores it on a storage device (hard drive).

Data that is software and as such is an application or program is something else entirely. It would have to be packaged. On Ubuntu software is packaged in the Debian package format (deb). The Debian package format would include information about how to install the software. The magic happens between the information in the Debian package and the Debian Package manager (dpkg installed in our systems) and APT (also installed on our systems).

[https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf](https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf)

[https://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php](https://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php)

[https://linuxize.com/post/how-to-use-apt-command/](https://linuxize.com/post/how-to-use-apt-command/)

An application developer would need to know about the Linux File System layout as well. I am assured that all of this is complicated. Which is why there are movements to simplify the process with an alternative type of package scheme. One group of developers are recommending something called Flatpacks and another group of developers are advocating Snaps. There may be other alternatives as well.

These different packaging schemes all have the purpose of simplifying the packaging process, adding greater security to the applications and reducing the time and effort in auditing the software code before it is allowed into a distribution's software repositories.

Regards

---

### Post by SeijiSensei on 2021-05-27
OK, first there aren't really "vendors" for most open-source software used on Linux machines. Perhaps you need to become acquainted with the whole open-source concept, for instance, [https://opensource.com/resources/what-open-source](https://opensource.com/resources/what-open-source).

Open-source applications are exactly what the name says.  They are distributed as source code and not as compiled binaries. A distributor like Ubuntu compiles the source into binary programs and packages them with something like apt or yum (RedHat and friends). Many programs are licensed with the "[GNU Public License]("https://www.gnu.org/licenses/gpl-3.0.en.html")" which requires that all software be distributed with the source code. Other software uses other, sometimes less restrictive, licenses like the [MIT License]("https://en.wikipedia.org/wiki/Category:Software_using_the_MIT_license")  or the [BSD license]("https://en.wikipedia.org/wiki/Category:Software_using_the_BSD_license").

---

### Post by rsteinmetz70112 on 2021-06-02
As I understand it for a third party application to be included in the repositories either Ubuntu must decide to maintain the application repository with their own resources or a third party maintainer, acceptable to Ubuntu must agree to maintain the repository in accordance with Ubuntu's policies.

Ubuntu usually back ports patches to the version in the repositories but doesn't add new versions within a release. The versions are incremented with a new Ubuntu release. This is for ocmpatibility and to avoid breaking existing installations with new or incompatible changes.

We use an application called Egroupware which used to be in the Ubuntu repositories but for reasons I don't entirely understand it was removed some years ago, the reason the developers
 gave was that Ubuntu wanted someone to step forward and agree to maintain the repositories and for whatever reason they could not agree. Eventually Egroupware offered their application through OpenSUSE repositories and it has been there ever since.

---

### Post by The Cog on 2021-06-02
Largely as  SeijiSensei says - programs are generally published as source code. Each distribution (Ubuntu or Red Hat for example) will compile the code for their distribution. In the process they will make sure the code uses the right other bits of software (e.g. C or Python library versions) and configure for the exact way that distribution likes to arrange different files in different directories. You can be fairly sure that if you take the application files from one distributon and try to run them on a different distribution it won't work right (or at all). It's a bit like having different versions of a program for each version of Windows, even when the program does the same thing.

---

### Post by anneranch on 2021-06-06
Thanks, with (rather typical )  detours from a subject -  " i  do not know much about this " and terminology  "vendors" the posts answered my question. 
However, I believe the "open source" concept   and the actual passing the vendors created code procedures and policies  are separate "objects". 
The question originated with  me implementing a software ( "vendor" intentionally not named - no advertising necessary ) by "install from Ubuntu " first. 
Then I downloaded from "vendor" and found out it really did not install supporting software as first install from Ubuntu did. 
Probably "policies" made the vendor's download "incomplete"  - so in that aspect the discussion mention about policies is valuable.

---

### Post by ActionParsnip on 2021-06-06
It sounds like you mean the dependencies of a package? This is how deb based systems work. Packages have dependencies that must be met if a package is to be installed. It sounds like you needed to install some deps to make the package you manually downloaded work. You can do this with
```

sudo apt -f install

```
Which will pull down the deps (if they are available) and then install the package you downloaded from the internet.

Is this what you mean?

---

