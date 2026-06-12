---
title: "Programs available to me"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Malikius on 2008-03-02
How do I find programs listings, that I can install on my new OS. I am just learning Linux. I am eager to see if I can install most of my programs that I have from Microsoft!  I hate Microsoft and want to use Linux instead. Is there a URL/site that I can look at to add programs to my virgin Linux install? I am going to install Linux on my laptop. Please assist me in this matter. 

Warmest Regards, Malikius.

---

### Post by uberlube on 2008-03-02
Well the add/remove in the menu is a big help as is the synaptic package manager. And if you want more check out getdeb and click n' run. Just google them. :)

---

### Post by uberlube on 2008-03-02
Oh ya and welcome to the community! Your gonna love it! :guitar:

---

### Post by Malikius on 2008-03-02
Thanks alot. I am eager to learn a new OS. What kind of programs can I load into Linux?

---

### Post by wednesday allfather on 2008-03-02
You can find replacements for almost anything you used in Windows that are equal or better (my opinion)

If you post what you are looking for, the good folks in the forum will tell you what they use.

If you just can't live without some .exe action in your life,  I suggest you check out WINE.  Search for it thru Synaptic.  

Good luck, and post again if you want some recommendations.

---

### Post by uberlube on 2008-03-02
There is pretty much an open source equivalent to every program you were using in Windows. For instance; 
Microsoft Office = Open Office
Windows Media Player = Amarok, Exaile, RyhtemBox, XMMS, etc.
IRC = IRC (such as Konversation, Xchat, etc.
Instant Messenger = Kopete, Pidgin, etc.

Your options are pretty much endless. Plus there are some really good games you can get such as Sauerbraten. A really good FPS. And you can still play some windows games and run some windows apps with WINE. Its a windows compatibility layer that os available in the repositories. You'll find out more as you go along. If you have any more questions, feel free to ask :)

---

### Post by Malikius on 2008-03-02
I am going to use my laptop first to get used to using Linux. I have the laptop wireless. Will I be able to use that function remotely? Like if I want to surf the web and get on Ubuntu forums from the comfort of my recliner? I love the background screens. I am so excited. :biggrin:
I am backing up my laptop now so I can put it on there.

---

### Post by uberlube on 2008-03-02
Yup wireless is usable as in any OS. You will probably have to install your driver to get it to work though so be prepared, Ill help you out if you need it. First you have to know:
What wireless card do I have?
And do I have the drivers on disk?

Once you have that your good to go. Even if you dont have them on CD, you can download the drivers online and install them using ndiswrapper.

---

### Post by Malikius on 2008-03-03
Thanks alot for all your help. I really do appreciate it. I will have loads of other questions, if that is alright? :)

---

### Post by Malikius on 2008-03-03
In the email program how do I setup my settings for gmail? What are the exact steps for gmail, PLEASE. You were right I have it on my laptop and I LOVE LINUX. Great job on creating it.

---

### Post by DaV|d on 2008-03-03
A good guide to setting up you mail client => [http://ubuntuforums.org/showthread.php?t=231724](http://ubuntuforums.org/showthread.php?t=231724)

Assuming you're using Evolution (default mail client on ubuntu),
skip this part if you're greeted with the setup assistant.

> 
Click on “Edit,” then “Preferences”

Click “Add”


---

### Post by Malikius on 2008-03-03
Having some trouble here. It is formatting to ext3 instead of ntfs. What am I doing wrong here. 

I set up the partition manager to format at NTFS and it is still formatting to ext3 or is that NTFS?:cry:

---

### Post by Malikius on 2008-03-03
Having some trouble here. It is formatting to ext3 instead of ntfs. What am I doing wrong here. 

I set up the partition manager to format at NTFS and it is still formatting to ext3 or is that NTFS?

---

### Post by Malikius on 2008-03-03
I am trying to reformat and setup my hard drive for NTFS format so I can use it with some of my windows files. How do I make this happen. I have used the partition manager to setup the formatting for NTFS and it keeps diverting it to ext3. How do I fix this problem? :(

---

### Post by oldos2er on 2008-03-03
Ubuntu will not install to an NTFS partition, if that's what you're trying to do.

---

### Post by ryanhaigh on 2008-03-03
If you want to create a partition to share between ubuntu and windows, when u are installing ubuntu just leave space for the data partition, and then boot into windows to create the partition and format it, creating a ntfs filesystem in ubuntu takes a long time compared to in windows.

---

### Post by Malikius on 2008-03-03
How about Fat32. How do I get my *.docs and other such files to work with Linux? Some of my music files will not play. What types do the installed software use in the music department. Do I have to manuelly convert them to another format? Please reply soon. I am getting frustrated here?

---

### Post by ryanhaigh on 2008-03-03
Ubuntu cannot install on fat either but it can read and write to both ntfs and fat. 
Docs etc will open in openoffice, for mp3's you will need to install resricted codecs, i recommend installing ubuntu-restricted-extras to get mp3, video codecs, flash and java. Have a look at this guide it may answer many of your questions.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by Malikius on 2008-03-03
also I can see the C drive just the file system. Sorry about all the questions. How do I mount the main drive. Do I do that before or after I format the drive or do I let the install program do that? If I go with ext3 will that work and can I then see the computer that will show up in the windows explorer or whatever it's called? 

What is the step by step of setting up the install so I can see the computer show up so I know that it is "on-line"? BTW, the gmail setup tutorial was a winner! 
Thanks.

---

### Post by ryanhaigh on 2008-03-03
Setting up ubuntu to dual boot with windows is explained in many places on the web as google will tell you. Here is one such example [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Once you have both operating systems installed then you can use ext driver from fs-driver.org in windows to access ubuntus ext partition and you can use ntfs-3g in ubuntu to access windows ntfs partitions.

---

### Post by Malikius on 2008-03-04
Now I have YET another problem. Well, two really. 

1. How do I switch from MSHOME network location to another where I can be in the same local network as the other 4 computers in my house. 

2. I, still can't get my wireless through Verizon router to work with my Broadcom 802.11 b/g Wlan card at least that is what I think it is. I have tried HP, Microsoft and the broadcom sites to try to find the driver that will work with my Ubuntu OS. 

I would appreciate an exact URL for the driver dor the broadcom so I can get this darned @#$&^%&, wireless to work. 

PLEASE HELP!!!!

Thanks in advance.

---

### Post by ryanhaigh on 2008-03-04
For your wireless check out the documentation here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
I think you can change the workgroup in system>administration>network shares (not on ubuntu at the moment so can't be sure)

You can also edit the config file directly the option to edit is workgroup as shown here
[http://www.faqs.org/docs/securing/chap29sec284.html](http://www.faqs.org/docs/securing/chap29sec284.html)

After you make these changes you might want to restart samba 

```
sudo /etc/init.d/samba restart 
```

---

### Post by Malikius on 2008-03-05
I have ABSOLUTLY no experience in writing code for this OS. I wouldn't know where to start. Is there an easy program I can download that will do that for me. And it ask me what Network I want to join, like in windows? And still having troubles with my BCM4306 802.11b/g wireless card to reconize the Verizon router. This is very upsetting and it is ticking me off. I might go back to Windows.

---

### Post by DaV|d on 2008-03-05
Regarding the workgroup, you can change it this way:

[COLOR="Red"]**Assuming you haven't changed /etc/smb.conf**[/COLOR]
(This might not work if smb.conf has been changed)

Go to *System > Administration > Shared Folders*

You will probably be prompted to enter a password. Enter your login password.

Afterwards, click on the *"General Properties"* tab and change the workgroup from there. 

Click close.

To see the results, open a terminal (*Applications > Accessories > Terminal*)
and write this:

```
sudo /etc/init.d/samba restart
```

You will be prompted for your password. Enter your login password & (hopefully) enjoy :p

---

### Post by Malikius on 2008-03-05
Thanks for the info.

---

### Post by Malikius on 2008-03-11
Thanks David, that worked nicely.

---

### Post by muximus on 2008-03-11
u can easily access an etx3 partition from windows as well.. thr r loads of tools available.. just google it.. i personally use ext2fsd.. i like it bcoz this way i can access an ext3 partition just like any other (fat/ntfs) on windows..

---

