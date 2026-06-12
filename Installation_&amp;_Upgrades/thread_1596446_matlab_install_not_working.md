---
title: "matlab install not working"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by cholericfun on 2010-10-14
hi

i needed a new harddrive and installed a new system (10.04 - previously 8.04) on it.
one of the things i wanted to install is matlab, however the installer doesn't do anything. I used the same iso image before on 8.04 and the install went smoothly.
i cant even get it to display the options.

so i untared all matlab related files out of my 8.04 backup.
can i just copy those files to the right places in my new system?
i guess not,but maybe there aren't that many things to modify.
Anyone any ideas / hints where to find more information.

---

### Post by cholericfun on 2010-10-15
hm, 

anyone any ideas at least how to get decent plots from octave, i dont really like the gnuplot version i.e. having to exactly code the plot before it is seen

---

### Post by thameera on 2010-10-29
First, you need to have sun java installed in your system. 
Second, you need to mount the CD/ISO with proper privileges.

FYI, here's how I installed it successfully: [http://goo.gl/6C02](http://goo.gl/6C02)

---

### Post by cholericfun on 2010-11-03
Hi
Thanks,

i tried this after installing sun-java like this:


```
1. sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
2. sudo aptitude update
3. sudo aptitude install sun-java6-jdk
```

however i still get nothing when executing

```
sudo ./install
```

as in the shell is finished in a splitsecond and returns.
Sorry, i really dont get it, whats going on?

---

### Post by thameera on 2010-11-04
What was the command you used to mount the matlab ISO?

---

### Post by cholericfun on 2010-11-04
i used 

```
sudo mount matu2k8a.iso /media/matlab/ -t iso9660 -o loop
```

as given in the link you wrote.

i also tried both running the installer from the iso and from its final install directory. Both times no change.

i might have just not everything installed that i need although i really cant think of anything

---

### Post by thameera on 2010-11-04
Two of my friends did exactly as mentioned in my post and successfully installed it. They were both using 10.10 however. Perhaps this has to do with the version. 

Can you give the output of the terminal after running sudo ./install?

---

### Post by dysonsphere23 on 2010-11-04
Hi,

your advice worked for me with MatLab2010b on Ubuntu 10.10.

thanks so much, as I been banging my head on my keybord trying to get it to work since the upgrade!

Only one issue:

I have to type sudo before the sh in order to get it to run.

Is there a way to get it to work without superuser privileges?

---

### Post by thameera on 2010-11-04
@dysonsphere23
AFAIK, the command "sudo chown -R ${USER}:${USER} ~/.matlab" mentioned in the blogpost is used for this purpose. If it fails, try to *chown* the /usr/local/matlab/bin/matlab as well. May work.

---

### Post by dysonsphere23 on 2010-11-04
hmmmmm,

I changed ownership in both those locations, verified by checking properties, but still get this:


"Fatal Error on startup: Failure loading desktop class"


when using the sh command.

using sudo sh starts it up just fine.

---

### Post by thameera on 2010-11-04
Try the solutions given in the following links:
[URL1]("http://www.mathworks.com/support/solutions/en/data/1-9IIO4C/index.html?product=ML")
[URL2]("http://ubuntuforums.org/showthread.php?t=887194")

---

### Post by thameera on 2010-11-04
<deleted>

---

### Post by dysonsphere23 on 2010-11-04
nope none of that worked.

tried the PATH and adding the symbolic link 

thanks for your help, don't mean to take up all your time on this.  I will dig a bit on my end and if I come up with anything will post the results.

---

### Post by thameera on 2010-11-04
Hmm, weird. 
And no problem at all. Please share the method if you could solve the issue.

---

### Post by dysonsphere23 on 2010-11-05
for what it's worth I am now (after restart) able to launch it from a launcher on my panel (dragged the matlab file to the panel) with the following command in the properties:

sudo /usr/local/MatLab/bin/matlab -desktop

the sh command does not work (splash screen appears and disappears)

IDK if it effects the functionality of it or not as I am very novice in MatLab, the only thing that looks strang is that the folders in the left sidebar are pale and hovering over them gves the message "this folder is not in your matlab path, double click to...."

---

### Post by cholericfun on 2010-11-08
after running ```
sudo ./install
``` theres no output at all,
no error messages or such so theres not much to help with searching for a solution

---

### Post by cholericfun on 2010-11-24
So anyone have any ideas whether its possible to just untar the matlab files from an old install and make it work?

---

### Post by cholericfun on 2010-11-30
Or any other ideas what may be causing the issue?

---

