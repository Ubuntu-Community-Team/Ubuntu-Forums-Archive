---
title: "no make command"
date: 2006-05-11
forum: Installation &amp; Upgrades
---

### Post by yairsuari on 2006-05-11
first i have to say that i am a begginer so take it slowly (thanks)
i am trying to install the intel fortran compiler using this guide:

[http://www.ubuntuforums.org/showthread.php?t=149579](http://www.ubuntuforums.org/showthread.php?t=149579)

after i save the make9 script i try to run it ( ./make9 intel-ifort9_9.0-031.i386.deb) but i get "command not found.
what do i do wrong?

thanks in advance

---

### Post by joft on 2006-05-11
Hi,

did you change make9's attributes to be able to execute it? You could do that by: ```
chmod +x make9
```.
And your script has to be in the same directory with the .deb file. Are you in that directory, while trying to execute it? (Do "ls" to see the contents of your current directory or look at the directory name in front of the command prompt).

---

### Post by yairsuari on 2006-05-11
this made the trick but now i get bad interpeter i will google it now

---

### Post by joft on 2006-05-11
Well, as you can see in the first line of the make9 script, it uses csh as it's interpreter. So you have to install "csh" first (sudo apt-get install csh).

---

### Post by yairsuari on 2006-05-11
so evrything looked like its working by i am still not seeing the idb and ifort commands anywhere.
what could be the reason?

---

### Post by joft on 2006-05-11
Hmmm, by looking at the script, you can see that the files will be installed into directories called /opt/intel/*/9.0 . So, I think, the binaries might be in subdirectories called "bin" (e.g. /opt/intel/*/bin).

The script mentioned in step 4 adds these paths to the PATH environment variable (while starting a bash, because then ~/.bashrc is executed).

Hmmm, perhaps in your case there is something wrong with the paths given in the second script .... e.g. does /opt/intel/fce/9.0/bin exist?

---

