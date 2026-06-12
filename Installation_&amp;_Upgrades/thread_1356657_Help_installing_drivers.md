---
title: "Help installing drivers"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Gedna on 2009-12-16
Hello.

im new at ubuntu, need some explanation i need to make drivers, but i dont know how, in terminal i tried but with no luck,
situation is this, i found my sound card drivers, and installation actions, 

Installation
These installation steps require you to have a configured and 

prepared kernel source installed.

Unpack the contents of the file to /usr/src
 *cd /usr/src; tar -xzf hdspm_090814.tgz*

Go into the new directory
 *cd hdspm*

Compile the driver
* make*

Install the new modules
 [I]make install
 modprobe hdspm[/I]


How to do this? when im trying to write  "cd /usr/src; tar -xzf hdspm_090814.tgz" in terminal i got an error :) i know it sounds stupid but i really dont know hot to make this, can some one please help me,

---

### Post by natravis on 2009-12-16
> **Gedna said:**
> How to do this? when im trying to write  "cd /usr/src; tar -xzf hdspm_090814.tgz" in terminal i got an error :) i know it sounds stupid but i really dont know hot to make this, can some one please help me,

Welcome! In order to write to the /usr directory, you need to use "sudo" to become a super user temporarily. I believe you will only need to input sudo one time, but if the lines do not work, press the up arrow and add sudo to the beginning of the line.

```
sudo mkdir /usr/src/hdspm
tar -xzf hdspm)090814.tgz /usr/src/hdspm
cd /usr/src/hdspm
make
make install
modprobe hdspm
```

You may need to use ```
./make
./make install
``` rather than just ```
make
make install
``` but someone other than I probably knows that answer.

Hope it's helpful!

---

### Post by Gedna on 2009-12-16
but where that hdspm_090814.tgz must be in order to take effect? in downloads? in my home folder, in desktop? because i still got errors when copying what you wrote

---

### Post by natravis on 2009-12-16
You should start in the folder where you originally downloaded the file. The mkdir command can be issued from anywhere and the tar command (as written) needs to be issued from the location of the downloaded file. Alternatively you could do
```
tar -xzf */path/to/download/*hdspm_090814.tgz /usr/src/hdspm
```
to issue that command anywhere.

Again, to write into the /usr folder you may have to use sudo before the tar command.

Please post any output when you receive an error message wrapped with the code tags (select the output text and click on the pound sign at the top of the input area). It will help us in determining why your error occured.

---

### Post by Gedna on 2009-12-16
emmm... damn i just cant make it... 

gediminas@gedimino:~$ sudo tar -xzf /path/to/download/hdspm_090814.tgz /usr/src/hdspm
tar: /path/to/download/hdspm_090814.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /usr/src/hdspm: Not found in archive
tar: Exiting with failure status due to previous errors
gediminas@gedimino:~$ 


i just dont get it how to make it, what im doing wrong? can some one write me the actual code becouse i cat understand where im doing wrong....

---

### Post by mkvnmtr on 2009-12-16
Are you sure you need to install drivers from an outside source? Have you checked under Hardware drivers in your Administration section?

---

### Post by Gedna on 2009-12-16
yes, i have RME 9632 alsa recognize the card, but i need to make drivers in order to get some sounds, i uninstalled pulseaudio, so i found this driver but i cant make it, im new to linux world, so... :)

---

### Post by natravis on 2009-12-16
When I said /path/to/download, you need to change that to the actual path where your file is downloaded. We can hold your hand but you have to use your brain! :P

---

### Post by Gedna on 2009-12-16
ok i set the actual path but i got this message

gediminas@gedimino:~$ sudo tar -xzf /home/gediminas/Downloads/hdspm_090814.tgz /usr/src/hdspm
tar: /usr/src/hdspm: Not found in archive
tar: Exiting with failure status due to previous errors
gediminas@gedimino:~$ 

what is wrong now? i have checked directory hdspm is created on usr/src but somethings wrong extracting files to it

---

### Post by natravis on 2009-12-16
I'm unsure what the correct syntax is for the tar command to unpack into a specific location so lets avoid that problem. You can use ```
sudo cp ~/Downloads/hdspm_090814.tgz /usr/src/hdspm
cd /usr/src/hdspm
tar -xzf hdspm_090814.tgz

```

This will copy the file into the correct directory that we already made then unpack it there. Then try the make commands within that directory.

---

### Post by Gedna on 2009-12-17
thank you for your patience :) ok heres what iv got

gediminas@gedimino:~$ sudo cp ~/Downloads/hdspm_090814.tgz /usr/src/hdspm
[sudo] password for gediminas: 
gediminas@gedimino:~$ make
make: *** No targets specified and no makefile found.  Stop.
gediminas@gedimino:~$ cd hdspm
gediminas@gedimino:~/hdspm$ make
make -Wall -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/gediminas/hdspm modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/gediminas/hdspm/hdspm.o
/home/gediminas/hdspm/hdspm.c: In function ‘hdspm_set_dds_value’:
/home/gediminas/hdspm/hdspm.c:992: error: implicit declaration of function ‘div64_32’
/home/gediminas/hdspm/hdspm.c: In function ‘snd_hdspm_probe’:
/home/gediminas/hdspm/hdspm.c:5382: error: implicit declaration of function ‘snd_card_new’
/home/gediminas/hdspm/hdspm.c:5383: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/gediminas/hdspm/hdspm.o] Error 1
make[1]: *** [_module_/home/gediminas/hdspm] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [default] Error 2
gediminas@gedimino:~/hdspm$ make install
make -Wall -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/gediminas/hdspm modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/gediminas/hdspm/hdspm.o
/home/gediminas/hdspm/hdspm.c: In function ‘hdspm_set_dds_value’:
/home/gediminas/hdspm/hdspm.c:992: error: implicit declaration of function ‘div64_32’
/home/gediminas/hdspm/hdspm.c: In function ‘snd_hdspm_probe’:
/home/gediminas/hdspm/hdspm.c:5382: error: implicit declaration of function ‘snd_card_new’
/home/gediminas/hdspm/hdspm.c:5383: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/gediminas/hdspm/hdspm.o] Error 1
make[1]: *** [_module_/home/gediminas/hdspm] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [default] Error 2
gediminas@gedimino:~/hdspm$ modprobe hdspm
FATAL: Module hdspm not found.
gediminas@gedimino:~/hdspm$ 


as far as i understand there is an error,  and in my attachement you can see that there is a tar file but its not extracted so maby thats causing the error, because there is nothing to Make, or make install.

---

### Post by natravis on 2009-12-17
> **Gedna said:**
> as far as i understand there is an error,  and in my attachement you can see that there is a tar file but its not extracted so maby thats causing the error, because there is nothing to Make, or make install.

You are correct. cp = copy, cd = change directory, tar=archive tool

So you need to think about what you want to do.

First, copy the file a location, second, unpack the file, third go into the directory where you unpacked things and finally, make the file.

---

