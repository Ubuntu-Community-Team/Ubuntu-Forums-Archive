---
title: "cannot install java for ubuntu"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by 12katia34 on 2011-11-19
Hey!
I am trying to set up a vpn client on my new computer (first time I use ubuntu). Installation requires Java which I cannot install
if I follow the instruction in terminal:
apt-get install sun-java6-jdk sun-java6-jre
the following error occurs
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

if I try to download manually, my comoputer tries to open the downloaded file (.bin) with the ububtu software center and tells me "this is not a software package"

Can anyone help?
Thank you
Kate.

---

### Post by darkod on 2011-11-19
To use apt-get you need to add sudo in front:
sudo apt-get install....

But you need JDK only for developing java applications. For running them you only need JRE, the runtime environment.

I am not sure you even need to install anything to run java, I think it has open java by default. I never needed to install any java packages.

---

### Post by raja.genupula on 2011-11-19
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```
sudo fuser -k -KILL /var/lib/dpkg/lock

```

do that in future cases also for such kind of issues.

 > if I try to download manually, my comoputer tries to open the downloaded file (.bin) with the ububtu software center and tells me "this is not a software package"
 
installing bin file with this commands from terminal

```
chmod +x filename.bin
./filename.bin

```
all the best.

EDIT : +1 for the above post   . yeah you gonna get that message when not using sudo .But even you use sudo also you got that error means use the 1st command i have given.

---

### Post by 12katia34 on 2011-11-22
> **darkod said:**
> To use apt-get you need to add sudo in front:
sudo apt-get install....

But you need JDK only for developing java applications. For running them you only need JRE, the runtime environment.

I am not sure you even need to install anything to run java, I think it has open java by default. I never needed to install any java packages.
yes, sudo gets me to install up to a certain point, then a message pops up in terminal (I need to agree to all the software liscences listed somewhere) and ends with an <ok> on which I cannot press and return doesn't work either. I had to kill the process to continue working in terminal, but now I cannot run the same command again. Bad Luck.

---

### Post by 12katia34 on 2011-11-22
> **raja.genupula said:**
> ```
sudo fuser -k -KILL /var/lib/dpkg/lock

```

do that in future cases also for such kind of issues.

 
 
installing bin file with this commands from terminal

```
chmod +x filename.bin
./filename.bin

```
all the best.

EDIT : +1 for the above post   . yeah you gonna get that message when not using sudo .But even you use sudo also you got that error means use the 1st command i have given.
Hey,
I am not sure how to enter your command, does is really go in two lines with a return in between? - Seperately the commands don't work, and they don't work together in one line either. - Where is my mistake?

first mistake
~$ chmod +x jre-6u29-linux-i586.bin
chmod: cannot access `jre-6u29-linux-i586.bin': No such file or directory

second mistake
~$ chmod ./jre-6u29-linux-i586.bin
chmod: missing operand after `./jre-6u29-linux-i586.bin'

third mistake
~$ chmod +x jre-6u29-linux-i586.bin./jre-6u29-linux-i586.bin
chmod: cannot access `jre-6u29-linux-i586.bin./jre-6u29-linux-i586.bin': No such file or directory

---

### Post by BC59 on 2011-11-22
From here

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

you can have a very good guide on how to install Java7 JDK.

---

### Post by BC59 on 2011-11-22
> **12katia34 said:**
> Hey,
I am not sure how to enter your command, does is really go in two lines with a return in between? - Seperately the commands don't work, and they don't work together in one line either. - Where is my mistake?

first mistake
~$ chmod +x jre-6u29-linux-i586.bin
chmod: cannot access `jre-6u29-linux-i586.bin': No such file or directory

second mistake
~$ chmod ./jre-6u29-linux-i586.bin
chmod: missing operand after `./jre-6u29-linux-i586.bin'

third mistake
~$ chmod +x jre-6u29-linux-i586.bin./jre-6u29-linux-i586.bin
chmod: cannot access `jre-6u29-linux-i586.bin./jre-6u29-linux-i586.bin': No such file or directory

I think to make it executable you just have to right click-properties and check -Allow Executing as a Program-.

---

### Post by darkod on 2011-11-22
> **12katia34 said:**
> Hey,
I am not sure how to enter your command, does is really go in two lines with a return in between? - Seperately the commands don't work, and they don't work together in one line either. - Where is my mistake?

first mistake
~$ chmod +x jre-6u29-linux-i586.bin
chmod: cannot access `jre-6u29-linux-i586.bin': No such file or directory

second mistake
~$ chmod ./jre-6u29-linux-i586.bin
chmod: missing operand after `./jre-6u29-linux-i586.bin'

third mistake
~$ chmod +x jre-6u29-linux-i586.bin./jre-6u29-linux-i586.bin
chmod: cannot access `jre-6u29-linux-i586.bin./jre-6u29-linux-i586.bin': No such file or directory

You need to put sudo in front for installing, the same as with apt-get.

---

### Post by 12katia34 on 2011-12-03
Hey darko,
I did type  sudo in front for all the three possibilities listed above. Can you please specify again, what exactly should I type into the terminal after "sudo"?
Thanks

---

### Post by 12katia34 on 2011-12-03
> **BC59 said:**
> I think to make it executable you just have to right click-properties and check -Allow Executing as a Program-.
hey, there is no properties option upon right clicking on the download file.

---

### Post by 12katia34 on 2011-12-03
> **BC59 said:**
> From here

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

you can have a very good guide on how to install Java7 JDK.
thanks, the java download solved itsself by a seperate pop up on my computer. It's now the binary file that stops me from having a vpn.
Thanks.
K.

---

