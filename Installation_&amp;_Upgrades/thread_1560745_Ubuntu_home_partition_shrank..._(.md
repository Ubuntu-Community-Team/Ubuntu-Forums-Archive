---
title: "Ubuntu /home partition shrank... :("
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by isaacalves27 on 2010-08-25
Hello :)

I hope you can give me some help on this..

I have adual boot installation with windows7 and Ubuntu Lucyd Lynx. I have some partitions:
/dev/sda5 linux Swap            - 4gb
/dev/sda6 ext4 mounted as /home - 10gb
/dev/sda7 ext4 mounted as /     - 32gb

and the rest of the 80gb hdd is the space used for win7 (i have cause I need to use some apps for working purposes).

the system is acting strange cause for 2 days ago i got a message that says that the /home partition is almost full there are only 452mb back.. and it shows the partition as being 1gb

Gparted for example shows the partition as it should be but shows anyway 8gb full and 1gb free... that is either what i have..

Any idea why for example nautilus shows me /home as being just 1gb capacity? I wouldnt know where to start looking at...

Thanks for your help

Isaac Alves:p

---

### Post by clrg on 2010-08-25
Please show me the output of

```
df -h
```

and 

```
du -kshc /home
```

---

### Post by isaacalves27 on 2010-08-25
Thanks for the quick reply :)

isaac@isaac-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              32G   19G   12G  63% /
none                  1,5G  316K  1,5G   1% /dev
none                  1,5G  1,3M  1,5G   1% /dev/shm
none                  1,5G   88K  1,5G   1% /var/run
none                  1,5G     0  1,5G   0% /var/lock
none                  1,5G     0  1,5G   0% /lib/init/rw
/dev/sda6             9,2G  8,3G  439M  96% /home

isaac@isaac-laptop:~$ sudo du -kshc /home
[sudo] password for isaac: 
du: cannot access `/home/isaac/.gvfs': Permission denied
8,2G	/home
8,2G	total


What exactly do these two commands do?

Isaac

---

### Post by clrg on 2010-08-25
Your /home partition definitely has a total size of 10GB. You currently have about 450MB free space. 

Delete some stuff to make free space. Your /home partition did not shrink, you just used up all the space.

Tip for the future: A 20GB / partition should be perfectly sufficient (my installation of Ubuntu currently uses 7.6GB on /). This should give you 12GB more for /home.

---

### Post by isaacalves27 on 2010-08-25
That happened to me in the past.. i was plyaing with Vbox and .. no more space..

But i have been more cautious now..

I now you shouldnt do this but..

If I start nautilus with sudo permissions thats what I have on my home folder: 1.061 items, totalling 882,6 MB...

---

### Post by clrg on 2010-08-25
Nautilus lies. Look at the output of the du command:

```
isaac@isaac-laptop:~$ sudo du -kshc /home
8,2G	/home
```

This means there are files and folders taking up 8.2GB of space. If you want to know how many files there are, run

```
find /home -type f | wc -l
```

---

### Post by isaacalves27 on 2010-08-25
with no root permission i cant run that

and with sudo..

isaac@isaac-laptop:~$ sudo find /home -type f | wc -l
[sudo] password for isaac: 
find: `/home/isaac/.gvfs': Permission denied
3923

thanks for hanging there :)

---

### Post by clrg on 2010-08-25
So you have 3923 files in /home.

---

### Post by isaacalves27 on 2010-08-25
mmm ok ill try to check were they are.. 

but just out of curiosity.. why do you think nautilus is syaing that my home folder has just 882,6mb?

---

### Post by clrg on 2010-08-25
I don't know why. I suspect you didn't select the right folder. Or it ignores hidden files. I really don't know. But I assure you, there are reasons why people use GNU tools (like du, df etc) for getting accurate filesystem usage instead of Nautilus & Co.

---

### Post by isaacalves27 on 2010-08-25
Ok 

Ill try to find out were my gb are :) but without nautilus i wouldnt know what to use .. I ll find out something

thanks for your tips :)

---

### Post by isaacalves27 on 2010-08-25
Du is a great tool

but i am still not understanding what is happening..

isaac@isaac-laptop:/$ sudo du -sh /home
du: cannot access `/home/isaac/.gvfs': Permission denied
8,2G	/home
isaac@isaac-laptop:/$ sudo du -sh /home/isaac
du: cannot access `/home/isaac/.gvfs': Permission denied
1,1G	/home/isaac
isaac@isaac-laptop:/$ sudo du -sh /home/lost+found/
16K	/home/lost+found/


I just have these two directories when i issue a ls -l.. where are the other 7gb?

---

### Post by isaacalves27 on 2010-08-25
forget it.. they are in the trash :(

---

### Post by clrg on 2010-08-25
Haha :lolflag:
Tip: If you want to delete files instead of moving them to the trash, press Shift-Del.

---

### Post by isaacalves27 on 2010-08-25
as a final thanks :D


isaac@isaac-laptop:/home$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              32G   19G   12G  63% /
none                  1,5G  316K  1,5G   1% /dev
none                  1,5G  260K  1,5G   1% /dev/shm
none                  1,5G   88K  1,5G   1% /var/run
none                  1,5G     0  1,5G   0% /var/lock
none                  1,5G     0  1,5G   0% /lib/init/rw
/dev/sda6             9,2G  1,3G  7,5G  15% /home
isaac@isaac-laptop:/home$ du -kshc /home
du: cannot read directory `/home/lost+found': Permission denied
du: cannot read directory `/home/.Trash-0': Permission denied
1,1G	/home
1,1G	total

---

