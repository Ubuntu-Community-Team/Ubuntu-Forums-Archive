---
title: "Would like to install Netbeans, Open JDK 7"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by Owen Thomas on 2013-01-12
Hello.

I am using Ubuntu 10.4, Netbeans 6.9, and Open JDK 6 for some time, and have otherwise had no need to upgrade any software on my Ubuntu environment. I would like to continue using Ubuntu 10.4.

However, I have recently come across some difficulty using Netbeans, and I believe this difficulty (IDE becomes preoccupied in syntax checking and becomes unresponsive as a result) may have been addressed in a later version of the software. I would also like to capitalise on some of the features JDK 7 appears to have with regard to generics.

Any quick and easy advice about upgrading Netbeans and Open JDK on my ubuntu environment would be of great help; I would rather prefer this process to be as uncomplicated as it can be.

Thanks,

  Owen.

---

### Post by darkod on 2013-01-13
It has been a while since I tried installing it, and never started doing any real development in it, but this is what I did:
1. Download the Oracle jdk7. Extract it in any folder where you like and note the path.
2. Install netbeans and in the GUI installer there is a field to put the jdk7 path (if I remember correctly). That will tell it to use the jdk7 you want.

That should be it.

On global level in ubuntu, if you want the whole system to use the jdk7 you have to update the java alternatives and specify to use the jdk7 instead of the openjdk. I don't remember the syntax correctly but it's easy to find it in google searching for update java alternatives in ubuntu, or similar.

---

### Post by Owen Thomas on 2013-01-13
Some things have changed a bit. I've decided that it was too complicated to install Netbeans 7.2 in Ubuntu 10.4, so I decided to upgrade Ubuntu to 12.4.

After upgrading Ubuntu, I noticed that my original version of Netbeans (6.9) was still installed. When I asked Ubuntu to install a later version of Netbeans, I noticed that Ubuntu only supported 7.0.

Regardless of this, I removed 6.9, because I happened along [this installation script]("http://netbeans.org/downloads/start.html?platform=linux&lang=en&option=javase"). Ignorantly, I ran it under my own user, so I deleted /usr/owen/<netbeans installation directory> and reran it as the super user.

Unfortunately, it appears that I can not now start Netbeans either from within the Ubuntu 12.4 Gui, or from a terminal.

Something's gone wrong, and I haven't any idea what that is. Please help.

Thanks,

  Owen.

---

