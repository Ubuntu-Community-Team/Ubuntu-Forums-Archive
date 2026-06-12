---
title: "Make an downloaded program function"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by chejose on 2010-05-19
I had been having problems with Thunderbird 3, so decided to install 2.0.0.24. I carefully cleaned out all the 3.0 files. So I downloaded it. Opened it with tar and can see that there is now a Thunderbird folder with all inside of it. But how do I make it run?

If I use "whereis" to locate the file to make it run, it says it is in /etc but i sure can't see it. There is a thunderbird file that seems to be the one in the thunderbird folder, but double clicking and mark "run" does nothing.

So I am lost.

Thanks for help.

José

---

### Post by oldos2er on 2010-05-19
There is a ppa for Thunderbird: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Also Ubuntuzilla: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by chejose on 2010-05-19
Thanks... but it is aimed at new versions. I cannot run apt-get because it tries to install the version 3, while I want to install the version 2.

The file came as a .tar.gz file. I opened it using tar and it formed folders with what I assume is the program. The problem is how to make it run.

José

---

### Post by ankit singh on 2010-05-19
Most of the application which are installed from source code are by running this commands

```
./configure
```*(which checks to see if you have the dependencies to allow it to  work, if not, you&#8217;ll have to manually install them)*
```
make
```*(actually compiles the source code)*
```
sudo make install
```*(actually installs the now compiled source code)*
```
clean install
```*(cleans the temp files used to compile the source code)*


while you&#8217;re in the folder that has the source files. It&#8217;s just a  simple CD (**c**hange **d**irectory) command  to jump into the folder that you uncompressed your saved source file to.  If you&#8217;re using Ubuntu and compiling files from source for the first  time, you have to install the build-essentials, run it from terminal:

```
sudo apt-get build-essential
```

---

### Post by ankit singh on 2010-05-19
oh i almost forgot to say that this method  will **not** work for everything, so  when you download a package, make sure to read the &#8216;README&#8217; or &#8216;INSTALL&#8217;  file, which should walk you though it step by step. Always follow the  provided documentation first, if you can&#8217;t get it working from using  that, then this is a secondary solution that should work for you fine.

is there any reason why u want to go to previous version?

---

### Post by wojox on 2010-05-19
It should be built already. Open a terminal and run:

```
thunderbird
```

That should run it. Then you can move it to your /opt directory and create a link in your menu or panel.

---

### Post by chejose on 2010-05-19
Thanks for all the feedback. I'll have to work on it for a while to see what I can do. I already tried running "thuderbird" in the terminal but it says that it is not installed yet.

I am going to try to shift to an older version since I have been struggling with the lastest version on more than one forum for days to solve a problem, but nothing. Since version 2 worked well in my earlier installation of Ubuntu (9.04) I hope this earlier version will work now.

Again, thanks.

José

---

### Post by oldos2er on 2010-05-19
Looks like I gave you the wrong URL. Try [https://help.ubuntu.com/community/Thunderbird#Thunderbird%202.0](https://help.ubuntu.com/community/Thunderbird#Thunderbird%202.0)

---

