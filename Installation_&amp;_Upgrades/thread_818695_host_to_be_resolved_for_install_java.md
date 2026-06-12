---
title: "host to be resolved for install java ?"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by leschaisesvides on 2008-06-04
hi

my machine is called andy and my connexion too ...(maybe not a good idea to start with !?):oops:

i'm trying to install java in the following folder :

andy@andy:~$ cd progs/java/
andy@andy:~/progs/java$ ./jre-6u6-linux-i586.bin
bash: ./jre-6u6-linux-i586.bin: Permission non accordée
andy@andy:~/progs/java$ sudo ./jre-6u6-linux-i586.bin
sudo: unable to resolve host andy
andy@andy:~/progs/java$ 

i've tried several things from different threads but no success and one thing that laways comes up is the "unable to resolve host andy" ...i'm a beginner in linux ....one (hard !:mad:) week ...

have you any ideas ? thanks in advance

andy

---

### Post by zvacet on 2008-06-05
```
cat /etc/hosts
```

Post output here.

---

### Post by leschaisesvides on 2008-06-05
thanks for help , here's what i get :


andy@andy:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 andy.home andy.free.fr

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
andy@andy:~$ 

:?:

---

### Post by Rocket2DMn on 2008-06-05
Change your second line to
```
127.0.1.1 andy
```
(or whatever to correct host name should be)
by running
```
gksudo gedit /etc/hosts
```

This is a known bug, see here for a list - [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by leschaisesvides on 2008-06-05
bjr/hi

i wroyte the code as proposed , thanks
i tapped enter and the cursur is under this following code :

andy@andy:~$ gksudo gedit /etc/hosts


but nothing happens ? 

i guess i'm doing something wrong ?

---

### Post by Rocket2DMn on 2008-06-05
Are you in a tty or something other that Ubuntu (with the GNOME desktop manager)?  You can use a command line text editor line nano
```
sudo nano /etc/hosts
```
When you're finished, to CTRL+X to exit and tell it to save at that time (press Y when prompted).

---

### Post by leschaisesvides on 2008-06-05
i'm on ubuntu hardy heron with the terminal 

that's all i know ....sorry :oops:

do you suggest passing by another/graphic programme ?

i'm not sure that i follow all the jargon yet !....lol i'm only on linux since last week....

thanks for any more explications / precisions

---

### Post by Rocket2DMn on 2008-06-05
Basically what I told you to do with the gksudo gedit command was open a text editor called gedit using root privileges (provided by gksudo, the graphical equivelant of sudo).  nano is a terminal based text editor, so we used sudo instead of gksudo.
See - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) and pretty much the rest of that site for some good reading.

Essentially, you need to edit that file to fix the second line to look like I said in post #2.  I'm heading off to bed in a minute.  If you don't get the problem fixed, just post back and I will get back to you in the morning.  Good luck!

---

### Post by leschaisesvides on 2008-06-05
ok cool / i'll try all that

moring here in france, off to work but i'll look into taht and get back in touch

cheers 

andy

---

### Post by jamesstansell on 2008-06-05
> **leschaisesvides said:**
> 
andy@andy:~$ cd progs/java/
andy@andy:~/progs/java$ ./jre-6u6-linux-i586.bin
bash: ./jre-6u6-linux-i586.bin: Permission non accordée


If you just want to install a private JRE using Sun's instructions, then
```
$ /bin/sh ./jre-6u6-linux-i586.bin
```
should work.  (I just did that this morning with the new Java 6 Update 10 beta release.)

If you want to install a system-wide java, then use Add/Remove Programs (or Synaptic, Adept or similar) to install the appropriate sun-java6-* packages.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) has some additional information, or feel free to post here again.

---

### Post by leschaisesvides on 2008-06-05
ok thanks also

my boss has just given me loads of stuff to get round before tommorrow but i'll get into all your suggestions in the morning (french time !) and i'll keep in touch

thanks to all 


andy

---

### Post by leschaisesvides on 2008-06-06
> **Rocket2DMn said:**
> Are you in a tty or something other that Ubuntu (with the GNOME desktop manager)?  You can use a command line text editor line nano
```
sudo nano /etc/hosts
```
When you're finished, to CTRL+X to exit and tell it to save at that time (press Y when prompted).

i still get the answer ...unable to resolve ..

---

### Post by leschaisesvides on 2008-06-06
yep ...i just understood and tried that ...i changed the second line of text and tehn i couldn't save the file ...not having the permission ...is that logical ?

thanks 

andy

---

### Post by leschaisesvides on 2008-06-06
hi

thanks again for help

i would prefer to install a system wide but i'll first try a private install (does that mean just for my connexion andy but not for all users in my computer (wife and kids for example ?)

have a good day

andy

---

### Post by leschaisesvides on 2008-06-06
> **jamesstansell said:**
> If you just want to install a private JRE using Sun's instructions, then
```
$ /bin/sh ./jre-6u6-linux-i586.bin
```
should work.  (I just did that this morning with the new Java 6 Update 10 beta release.)

If you want to install a system-wide java, then use Add/Remove Programs (or Synaptic, Adept or similar) to install the appropriate sun-java6-* packages.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) has some additional information, or feel free to post here again.

hi again i tried the "private" way --- here's what i got :


[I]andy@andy:~$ cd progs/java/
andy@andy:~/progs/java$ $ /bin/sh ./jre-6u6-linux-i586.bin
bash: $ : commande introuvable[/I]

or (i tried from my root ...if that's how we call that ?)


[I]andy@andy:~$ $ /bin/sh ./jre-6u6-linux-i586.bin
bash: $ : commande introuvable
andy@andy:~$ [/I]

sorry to not manage this very well ](*,)

for information too ; when i connect i no longer have access to the add and remove program in the applications menu !! 

any help is welcome thanks very much

have a good day

andy

---

### Post by jamesstansell on 2008-06-06
I would recommend that you try the system install first.  For java applications you want the sun-java6-jre package, or for the java browser plugin you want the sun-java6-plugin package.

Use the add/remove programs tool or the synaptic package manager, whichever you prefer.

---

### Post by leschaisesvides on 2008-06-07
hi thanks again

i don't have the add/remove tool in my 'applications' menu anymore (i did before ?!)

and apparently synaptic package manager is not installed yet (so as i don't have the add / revmove tool .....) ? seems to be a vicious circle ? don't you think ?

i'm a bit lost

andy

---

### Post by Rocket2DMn on 2008-06-07
Synaptic would be accessed from System->Administration->Synaptic Packages Manager.  Is it really not there?

---

### Post by leschaisesvides on 2008-06-07
nothing at all with the name synaptic in this menu !! heeeeelp !

getting odder by the minute ?

thanks for your help and ideas, we'll get there yet !

andy

---

### Post by Rocket2DMn on 2008-06-07
Try opening a terminal and running
```
sudo apt-get install synaptic
```

---

### Post by leschaisesvides on 2008-06-08
this is what i get back :



andy@andy:~$ sudo apt-get install synaptic
sudo: unable to resolve host andy
andy@andy:~$ 



andy

---

### Post by Rocket2DMn on 2008-06-08
Can you please post your /etc/hosts file again, it seems that the problem was not fixed with it
```
cat /etc/hosts
```
Also see: [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by leschaisesvides on 2008-06-08
hi

no it wasn't / i can change the hosts file but then cannot save it (without rights )


andy@andy:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 andy.home andy.free.fr

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
andy@andy:~$ 

thanks for any advice

andy

---

### Post by Rocket2DMn on 2008-06-08
Run
```
gksudo gedit /etc/hosts
```
and change the line from
```
127.0.1.1 andy.home andy.free.fr
```
to
```
127.0.1.1 andy
```
Save and close, then run
```
sudo apt-get update
sudo apt-get upgrade
```
You said earlier that nothing happens when you ran the first command I listed here - if that is still the case, can you please explain?  Are you at a full screen terminal?  Are you using Kubuntu instead of Ubuntu?  If you can't figure it out, please post a screenshot.

---

### Post by leschaisesvides on 2008-06-08
having typed the first command ------     gksudo gedit /etc/hosts

this is what i get ....with the cursor flashing under the line of code ans apparently nothing happening ?

andy@andy:~$ gksudo gedit /etc/hosts

---

### Post by leschaisesvides on 2008-06-08
here is my screen shot

i am on ubuntu hardy heron

thans v much ...we may get there yet !

andy

---

### Post by Rocket2DMn on 2008-06-08
OK, I'm going to have you reboot into the recovery mode kernel to fix this problem.  Reboot your computer, and at the GRUB screen, choose the second option, it will have (recovery mode) at the end.  If prompted, choose to go to the root recovery terminal.  Once there at the full screen terminal, run
```
nano /etc/hosts
```
You will then have a text editor that you can navigate around by using the arrow keys.  Change the line from
```
127.0.1.1 andy.home andy.free.
```
to
```
127.0.1.1 andy
```
by deleting that extra stuff.  Then do CTRL+X, hit Y, then hit Enter.  You should now be back at the prompt - tell the computer to restart by running
```
reboot
```
Let the system restart normally, and your problem should be fixed.

---

### Post by leschaisesvides on 2008-06-08
all that went fine , thanks

should i now try the following code to install synaptics , as i still don't have the add remove thing in the applications menu ?

sudo apt-get install synaptic

thanks so much 

andy

---

### Post by Rocket2DMn on 2008-06-08
Sure, you can always right click the menus area and select Edit Menus.  It could be that for some reason Synaptic is not checked to be visible.  There are some that are disabled by default which you can feel free to enable, but Synpatic should be visible.
I'm going to bed here in California, but I'll get any response you post in the morning.  Good luck.

---

### Post by leschaisesvides on 2008-06-08
ok thanks i'll try that

was in LA last year ...my brother in law lives in venice beach

your lucky folk !!

well i guess the sun is a last out in orléans / france today

i'll keep you in touch

andy

---

### Post by leschaisesvides on 2008-06-08
hi 

this is now the answer i get with the cat hosts command : looks ok now ?



[I]andy@andy:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 andy

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
andy@andy:~$ [/I]

but in the edit menus place i can tick the "add remove program" but it "un ticks" itself within a second !! i guess i still don't have the necessary rights on my machine ? so anyway it doesn't appear in the menu

here's a screen shot (in joint file) of my users (who is the root ?)

i'm off to belgium :) for 5/6 days for work and may not be on the net ...and will be away from this machine anyway

if you have any ideas .....i'm sure you do !! thanks in advance ....i'll try all possible next weekend

thanks again for all your help =D>, hi to california

andy

---

### Post by Rocket2DMn on 2008-06-08
OK, open a terminal and run
```
groups
```
This will list the groups your username is a member of.  Here is a sample output from my computer:
```
connor@lappy686-mk2:~$ groups
connor adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin fuse sambashare
```
If the group "admin" is not listed, reboot again into the recovery mode terminal and run
```
useradd -G admin andy
reboot
```
After a normal reboot, to check a couple of things, I want you to post the output of this command:
```
sudo cat /etc/sudoers
```

---

### Post by leschaisesvides on 2008-06-08
hi this is what i got back

[I]andy@andy:~$ sudo cat etc/sudoers
[sudo] password for andy: 
andy is not in the sudoers file.  This incident will be reported.
andy@andy:~$ [/I]

for information when i did useradd -G admin andy

the reply was something like user andy already exists

thanks ...

andy

---

### Post by Rocket2DMn on 2008-06-08
Forgive me, that command only works when the user doesn't exist yet.  Here is what needs to be run from the recovery mode terminal:
```
usermod -a -G admin andy
```
You should then be able to use "sudo".

---

### Post by leschaisesvides on 2008-06-08
your simply the BEST ! as they say here....."vous êtes le meilleur" thanks very much for your time and patience

apparently all is back to use no problem ...i'll just put in java now ....with all the exchanges i've learnt a lot ...and so should get on ok !!


merci beaucoup !!

:razz:=D>:grin:):P

andy

---

