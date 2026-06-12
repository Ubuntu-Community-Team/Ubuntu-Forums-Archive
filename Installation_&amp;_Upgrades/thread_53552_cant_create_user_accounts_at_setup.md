---
title: "cant create user accounts at setup"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by fester2001 on 2005-08-01
hey trying to install ubuntu 5.04 onto my laptop
the installation goes fine untill i get to setting up user accounts,
it asks for my full name then username then password but when i type my password it just goes back to the start asif i havent done anything and no user account is created.

i also tryed running adduser from a terminal but it kept saying that it was setting up the account and then it would say invalid group and delete it :/

Thanks

---

### Post by frodon on 2005-08-01
I had this problem installing ubuntu on a laptop, it's make me crazy but after 4 attemps re-installing ubuntu  ..... it works.
I don't know why there is this problem but if you try several times it will work. Maybe the install CD could be improved on this point, I already met this problem with 2 different computers. 
Is there a place where I can report this bug ?

---

### Post by fester2001 on 2005-08-01
i have tryed version 4 about 6 times and version 5 twice so far with no luck

---

### Post by frodon on 2005-08-01
Arg .... you're not lucky !
Last time I met this bug I spend all my afternoon to install ubuntu. Did you take care to not choose the same name for your computer and your user ? (I know it's a stupid question but ...)
Any other ideas ... someone ?

---

### Post by fester2001 on 2005-08-01
yep did that

---

### Post by burakc on 2005-08-01
Hi all!

I've faced exactly the same problem and I guess I found one reason (and solution) what causes this problem.

Firstly, I've used a downloaded Kubuntu 5.04 install CD, and used the Turkish language selection.

My problem was apperantly caused the by the non ASCII character "Ç" in the full name (not the user name) of the first user I entered during the setup. When I entered a full name without the non-ASCII all went fine.

I wonder if this may be the problem with you too?

I think this is a rather serious problem from the user's point of view, because a first timer installer (e.g. me) may become very frustrated as there is not much help from the installer for this problem. 

So, I've collected some evidence for my problem if it maybe helps to sort the situation. Maybe this should be posted to a different category to catch the maintainer's attention? I'm a newbie, so any ideas?

Anyhow, I'm no Linux wiz - not even a proficient user, but I think the problem is in the order for installing the localization.

Here is what the second console shows during the faulty installation:

...
local 'tr_TR.UTF-8' not available
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset)
	LC_ALL = (unset)
	LANG = "C.UTF-8"
     are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
local 'tr_TR.UTF-8' not available
Generating locales...
	tr_TR.UTF-8... done
	en_US.UTF-8... done
Generation complete.
Reading package lists...
Building dependency tree....
Suggested packages...
...

---

### Post by fester2001 on 2005-08-02
so in simple terms what do i do to make it work?

---

### Post by fester2001 on 2005-08-02
[http://bugzilla.ubuntu.com/show_bug.cgi?id=9966](http://bugzilla.ubuntu.com/show_bug.cgi?id=9966)
it didnt like me having my /home on a difrent partition

---

### Post by burakc on 2005-08-02
Ok, I checked that page, it seems there's a problem of some sort with user creation.

From my understanding the question is: Does your first account's "full name" have any non-ASCII characters?

If yes, than don't use any because it seems to me that it may cause a problem! If no, I don't know what causes your problem. Sorry..

---

### Post by fester2001 on 2005-08-02
there where no asci characters in there
but when i just left /home on / insted of on another partition it worked ](*,)

---

### Post by Corlian on 2005-08-16
I had this problem tonight.  I used only regular ascii characters in the user information.  The problem was definitely the partitions.  I wanted a FAT32 partition, and it set it to /home as default, and this being my first Linux installation I didn't know any better.

I reinstalled, and in the partitioner I made sure the FAT32 partition didn't point to /home, and now I'm writing this from Kubuntu.

So, it seems future versions of the installer shouldn't set other partitions to /home by default.

---

### Post by fester2001 on 2005-08-18
[QUOTE=Corlian]I had this problem tonight.  I used only regular ascii characters in the user information.  The problem was definitely the partitions.  I wanted a FAT32 partition, and it set it to /home as default, and this being my first Linux installation I didn't know any better.

I reinstalled, and in the partitioner I made sure the FAT32 partition didn't point to /home, and now I'm writing this from Kubuntu.

So, it seems future versions of the installer shouldn't set other partitions to /home by default.[/QUOTE]
 yer i did the exact same thing

---

