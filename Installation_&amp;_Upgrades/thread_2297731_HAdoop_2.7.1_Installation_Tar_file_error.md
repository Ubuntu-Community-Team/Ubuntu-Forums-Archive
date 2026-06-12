---
title: "HAdoop 2.7.1 Installation Tar file error"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by vivek26 on 2015-10-06
This is what am getting when am trying to run following command . Kindly suggest what to do , i am new to ubuntu ,my hadoop is downloaded in /home/Downloads  . Tried moving the already zipped file but i get an error no such file exits .
   ```
vivek@vivek-HP-15-Notebook-PC:/usr/local$ sudo tar xzf hadoop-2.7.1.tar.gz 
[sudo] password for vivek:  tar (child): hadoop-2.7.1.tar.gz: 
Cannot open: No such file or directory tar (child): 
Error is not recoverable: exiting now tar: 
Child returned status 2 tar: 
Error is not recoverable: exiting now

```

---

### Post by howefield on 2015-10-06
Try running the command from the Downloads folder instead of /usr/local/ (or successfully move the file to /usr/local/ first if that is where it needs to be).

```
cd ~/Downloads
```
```
sudo tar xzf hadoop-2.7.1.tar.gz
```

---

### Post by vivek26 on 2015-10-06
ok i did that but how do i know that file is extracted and moved to /usr/local/  ? because it needs to be there only . Moreover i wana ask how to open 
[h=2]$HOME/.bashrc file and edit it for a new user hduser ?[/h]

---

### Post by howefield on 2015-10-06
> **vivek26 said:**
> ok i did that but how do i know that file is extracted and moved to /usr/local/  ? because it needs to be there only .]

To move the file to /usr/local/ do..

```
sudo cp ~/Downloads/hadoop-2.7.1.tar.gz /usr/local/
```

then run the extract command.

```
sudo tar xzf /usr/local/hadoop-2.7.1.tar.gz
```

Check the files present in the folder with...

```
ls -l /usr/local/
```

---

### Post by vivek26 on 2015-10-06
Thanks a lot sir , it wouldnt be possible without internet community for me to install hadoop .. Now am setting up the $HOME/.bashrc file and further steps , if i struck somewhere i will ask for your help .

---

### Post by vivek26 on 2015-10-06
"hadoop-env.sh" opened this file using gedit to edit/modify the java home variable but this file is empty ... What to do ? am using java 8 by oracle downloaded through ppa:webupd8team/java

---

