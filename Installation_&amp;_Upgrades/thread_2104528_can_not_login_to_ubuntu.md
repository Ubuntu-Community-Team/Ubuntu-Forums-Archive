---
title: "can not login to ubuntu"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by saiedov on 2013-01-13
Dear 

I tried to upgrade Ubuntu from 12.04 LT to 12.10 but unfortunately the power is down,


then i switch on my laptop after electricity back to continue; but now it is giving ubuntu Logo without any  responses .


Note:
1) I use Windows 7 Ultimate
2) I have Dos Prompt to select which Operation System will Work
either Windows as Default or by Ubuntu

Thanks in advance,


Saied

---

### Post by darkod on 2013-01-13
By Dos prompt do you mean the windows bootloader or the grub2 ubuntu bootloader? If you have the windows bootloader, do you have a wubi install inside windows or proper dual boot with ubuntu on its own partition?

---

### Post by saiedov on 2013-01-13
> **darkod said:**
> by dos prompt do you mean the windows bootloader or the grub2 ubuntu bootloader? If you have the windows bootloader, do you have a wubi install inside windows or proper dual boot with ubuntu on its own partition?


first of all, i  pleased for your replay and support,

but i am still junior and do not have knlowdge for your terminlogy


for your concern the main o.s. Is windows 7 and it is working fine till now but my ubuntu failed to login   

i hope this clear for you.

---

### Post by saiedov on 2013-01-13
I HAVE WINDOWS 7 64-BIT AND I DO NOT KNOW FROM YOUR WHERE GET THIS INFORMATION OF  wubi install inside window

---

### Post by darkod on 2013-01-13
Boot the computer with the ubuntu cd in live mode (Try Ubuntu option), open terminal and post the output of this command:
```
sudo parted -l (that's small L)
```

---

### Post by grahammechanical on 2013-01-13
Some people use this method for trying out Ubuntu.

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows]("http://www.ubuntu.com/download/help/install-ubuntu-with-windows")

But when they post a problem on this forum, they forget to tell us that they have installed Ubuntu inside Windows. To give accurate advice we need accurate information.

Regards.

---

### Post by saiedov on 2013-01-13
> **darkod said:**
> Boot the computer with the ubuntu cd in live mode (Try Ubuntu option), open terminal and post the output of this command:
```
sudo parted -l (that's small L)
```



Ok but how i can write this command, if the system does not give me privilege

---

### Post by saiedov on 2013-01-13
my question is, how i can open terminal to post any command !!??

---

### Post by darkod on 2013-01-13
Read my post very carefully, again. If you can't do even this basic procedure, there is not much we can do to help you because we don't know magic. :)

Take your ubuntu cd and boot the computer with it, from the cd-rom, not the hdd. Your computer can boot from a cd-rom even if the hdd installation is totally screwed. Selecting the Try Ubuntu option from the main menu of the ubuntu cd, will load a live session running from the cd. That is how you can open terminal.

The more you speak, the more it looks like you have only wubi inside ubuntu, since if you installed it properly from the cd you would know how to boot a computer with a cd.

---

### Post by saiedov on 2013-01-13
yes , i make it this option for Booting from CD.


but this cs gives two option without runit under Dos Shell


the system now open by this method:

Install Ubuntu

or Try it from CD


the cd is contain WUBI, if there is way to create new CD for Repair Ubuntu

---

### Post by darkod on 2013-01-13
If the re is the option Try, the cd is not only wubi, it's the full ubuntu cd. Select the Try option and see if that loads the live session.

---

### Post by saiedov on 2013-01-13
Ok darkod, so where is option of Terminal, do you want me to make install again or select other option of try from CD, bu thsi GUI not Dos Prompt


thanks a lot

---

### Post by saiedov on 2013-01-13
do you know which key in keyboard to see the message , i mean like Pause Key

so easy fro you what is the problem i am facing to reboot without CD

---

### Post by saiedov on 2013-01-13
the Booting CD , it should be CD or DVD.


Becuase i Burn ISO on DVD not CD

if this make any different

Kindly advise,


Saied

---

### Post by saiedov on 2013-01-13
after restart my laptop

I PREES F12 TO CAN SELECT FROM WHHC DRIVE FOR STARTING BOOT

I SELECTED   == >     DVD


THEN I PRESS CTL + ALT + T

IT GIVES :

BOOT: 

THEN I WROTE THIS COMMAND 


BOOT: stud Parted -l
BOOT: bad Kernal 



what is your suggestion in this case


best regards,

---

### Post by darkod on 2013-01-13
Don't press the Ctrl+Alt+T. Let the dvd boot until you see a main menu asking you if you want to Try Ubuntu or Install Ubuntu. Select Try and let it boot the live session.

Inside the live session open terminal and execute the command mentioned earlier.

---

### Post by saiedov on 2013-01-13
ok,

i wrote this command

sudo parted -l

i got the following:

Model: ATA ST9640320AS
Disk /dev/sds: 640G
Sector Size (Logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End          Size           Type           File System        Flags
1            1094kB   106MB      105MB        Primary       fat16                 diag
2            106MB    15.8GB     15.7GB        Primary       ntfs                   boot
3            15.8GB    329GB      313GB         Primary       ntfs     
4            329GB     640GB      312GB         extended                             lba
5            329GB     535GB     207GB          logical         ntfs
6            535GB     640GB      105GB         logical         ntfs

Warning Unable to open /dev/sr0 read-write (Read Only File-System). dev/sr0
has been opened read only.
Error: can't have a partition outside the Disk!

---

### Post by darkod on 2013-01-13
You have only wubi inside windows, not a proper dual boot. That will make it little bit more complicated to try and save it. If you don't have any important data inside, you might as well remove this wubi installation from windows Programs, and install it again.

Also, the 12.04 version is LTS which means it has long time support. You don't have to upgrade it to 12.10 just because it's newer.

If you want to try and save this one, try booting the computer, select ubuntu in the first boot menu and that should show you second boot menu. In that second boot menu select the recovery mode option of ubuntu, not the standard. That should show you the recovery mode menu. In there select Network, and after that in the same menu Drop to root shell.

That should open a terminal for you, as root. In there try running these two commands:
```
dpkg --configure -a
apt-get install -f
```

After they are finished, reboot and try booting your wubi as normal.

---

### Post by saiedov on 2013-01-14
thank you DARKOD

FIRST, I WANT TO INSTALL 12.10
SECOND, HOW I CAN SELECT RECOVERY MODE
THIRD, HOW I REMOVE THE WUBI IT IS INSIDE DVD AND I BELEIVE I CAN NOT REMOVE IT OR RENAME IT.

---

### Post by saiedov on 2013-01-14
Can some one guide me to fix this error for booting ubuntu

---

### Post by keheikev on 2013-01-14
I think your question is how to run "terminal" from the cd. From the cd select try  linux which will start a live environment which only lives in your ram unless you have it save some persistent files. I believe under the dash menu it should have the program terminal which you need to start.
Then run those commands by default the sudo will not require a password for a live install.
hope that helps
Kevin
;)

---

### Post by saiedov on 2013-01-15
> **keheikev said:**
> I think your question is how to run "terminal" from the cd. From the cd select try  linux which will start a live environment which only lives in your ram unless you have it save some persistent files. I believe under the dash menu it should have the program terminal which you need to start.
Then run those commands by default the sudo will not require a password for a live install.
hope that helps
Kevin
;)


Dear keheikev

thank you for your help, my problem is how to fix Problem of Ubuntu 12.04 LT when starting , becuase now it is showing black screen only

i hope this clear for you and our helper

---

### Post by keheikev on 2013-01-15
I the muddiness came from you referring to the boot-loader menu as a DOS prompt in your initial post.Most dual-boot or multiboot systems display this boot-loader menu at startup.
 Are you able to run the terminal commands from the live cd? First we are trying to confirm you do not have a WUBI install which would require a different type of troubleshooting.
 That will help diagnose whats going on. You should be able to post to the newsgroup any output from the live cd as it will allow connecting to the internet.
Kevin

---

### Post by darkod on 2013-01-15
The install is wubi, that is already confirmed. Look at the partitions list in post #17. No linux partitions.

I told you what you can try in post #18. Sorry, but if you can't follow that, try asking some friend who knows more about computers to help you follow those instructions. It doesn't matter how many times we repeat them here, you will still have to do them yourself, we can't do them for you.

You have everything you need in post #18. Did you try to do it at all? Where did you get stuck?

Don't just repeat asking what to do, you have few suggestions. Tell us whether you have started following some procedure, and if you did, where did you get stuck.

---

### Post by keheikev on 2013-01-16
whoops sorry somehow I missed those posts this o/s browser combination was kind of jumpy in rendering the group.
Kevin

---

### Post by saiedov on 2013-01-17
OK GENTLEMEN


if repair the booting not fix my problem.


I prefer to remove Ubuntu permanently from my machine, and install it again better than repair it and take long time.

so how i can do that


Thanks,

Saiedov

---

### Post by darkod on 2013-01-17
Boot windows and go into Control Panel - Programs (on XP it's called Add/Remove Programs).

Find the ubuntu program, click on it and select Uninstall/Remove just like you remove any windows software.

---

### Post by saiedov on 2013-01-18
as the attached file, the system will remove everything related to Ubuntu with all updated before

is it right, so no harm after this one,


and again i will install the new release  


Kindly Advise me


thanks for every one help me

---

### Post by darkod on 2013-01-18
Yes, that's it. It should remove everything, but I don't use wubi so I can't really say. Sometimes there might be bits and pieces left.

---

