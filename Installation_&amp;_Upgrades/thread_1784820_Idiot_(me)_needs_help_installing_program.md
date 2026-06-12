---
title: "Idiot (me) needs help installing program"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by theTemest on 2011-06-17
I am absolutely clueless on how to install an application:( (other than by using the built in installer). I would really like to try the new Gimp single window application, but have absolutely no idea on how to install it.
I have downloaded the TAR file (gimp 2.7.2) and its MD5. I am using Ubuntu 10.10. Can someone point me to a URL where it describes the install process in detail or spell it out for me? That would be greatly appreciated.

---

### Post by apollothethird on 2011-06-17
> **theTemest said:**
> I am absolutely clueless on how to install an application:( (other than by using the built in installer). I would really like to try the new Gimp single window application, but have absolutely no idea on how to install it.
I have downloaded the TAR file (gimp 2.7.2) and its MD5. I am using Ubuntu 10.10. Can someone point me to a URL where it describes the install process in detail or spell it out for me? That would be greatly appreciated.

With many tar balls you will run "./configure" to prepare the package for compiling.

Then you would run "make" to compile the package.

Then you'll run "make install" to install the package.

Sometimes you have to run "make clean" or "make distclean" to remove partial compiled components.

```
make clean
./configure
make
make install
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by oldos2er on 2011-06-17
There are instructions in gimp2.7.2/INSTALL
If this is your first time compiling source code, it might be a challenge.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by ajgreeny on 2011-06-17
There is a ppa, I think with the version of gimp with a single window;  I will try and find it and report back if I can pass on any more info.

I did try it myself and it was OK, but I don't really mind the separate window layout, and in the version I tried you needed to set the single window layout at each start of the application; it did not stick when closed down.

EDIT:
OK, here you are:-
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

---

### Post by theTemest on 2011-06-17
Thanks for all the replies.

oldos2er- This is my first time and what you see as a challenge is what non-Linux users call command line paralysis.

When I get home I will try each and every suggestion. I really do want to learn code and the use of command line.

Again, thanks to all and I will post back when any progress or success or further confusion!!!

---

### Post by xcommunistx on 2011-06-17
First of all, search in Synaptic Package Center for Nautilus-Open-Terminal...
Now Open the .Tar file and Put everything which is in this .Tar in One Folder...
Go to the Folder, Right-CLick and ''Open in Terminal''...
Now Type ''make''...
Then Type ''make install''
This is all, now it should be installed if you search it in Applications...!
Otherwise just search for it in the Software-Center!

---

### Post by hakermania on 2011-06-17
I just want to point out that the title shows extreme self-confidence!

Usually the install process is described either in INSTALL or README file inside the tar.gz file.

---

### Post by theTemest on 2011-06-18
> **hakermania said:**
> I just want to point out that the title shows extreme self-confidence!
:lol: Now that's funny!!

Simply tried to avoid the assumption that I knew anything about command line or code. And yes, I did open the install file and knew immediately that I needed help. You ever tried to read and understand Japanese? If so, welcome to the club.

Getting ready to give it a go. Again, thanks to everyone. And might I add that except for a few select forums for Vista/Win 7, people are so damn much friendlier and willing to help in Linux/Ubuntu forums.

---

### Post by lightstream on 2011-06-18
Tempest - make sure you start with ajgreeny's suggestion, namely adding the PPA to your sources list (do it via Update Manager > Settings)

This will let you install a pre-compiled GIMP from an alternative repository that holds the single-window version.

The other guys are telling you how to compile GIMP from source (you have after all downloaded the source tar ball!). I'm pretty sure this is not something you will find to be a walk in the park!

But let us know how you get on - I find the multi-window GIMP a nuisance so might give this version a try if it's any good.

---

