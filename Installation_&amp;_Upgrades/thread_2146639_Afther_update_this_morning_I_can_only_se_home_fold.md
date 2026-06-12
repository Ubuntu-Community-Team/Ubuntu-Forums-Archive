---
title: "Afther update this morning I can only se home folder"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2013-05-19
I have update this morning since that I only can se /home nothing else.
for example files, users everything else is missing
help.

---

### Post by 2F4U on 2013-05-19
Are you still able to login with your normal user? Can you open a terminal, type ls -al /home and post the output?

---

### Post by hoboy on 2013-05-19
> **2F4U said:**
> Are you still able to login with your normal user? Can you open a terminal, type ls -al /home and post the output?

Here is it.
luc@luc-Satellite-A300D:~$ ls -al /home
total 20
drwxr-xr-x   3 root root  4096 Aug  7  2012 .
drwxr-xr-x  25 root root  4096 May 19 10:30 ..
drwxr-xr-x 124 luc  luc  12288 May 19 22:02 luc

---

### Post by jamesisin on 2013-05-19
What is the output from ***ls -al /***?

---

### Post by hoboy on 2013-05-19
> **jamesisin said:**
> What is the output from ***ls -al /***?

  ls -al /?
ls: cannot access /?: No such file or directory

---

### Post by hoboy on 2013-05-19
> **hoboy said:**
> ls -al /?
ls: cannot access /?: No such file or directory

----------------------------------------------------------------------
 ls -al / ?
ls: cannot access ?: No such file or directory
/:
total 112
drwxr-xr-x  25 root root  4096 May 19 10:30 .
drwxr-xr-x  25 root root  4096 May 19 10:30 ..
drwxr-xr-x   2 root root  4096 May 14 07:01 bin
drwxr-xr-x   3 root root  4096 May 19 10:30 boot
drwxr-xr-x   2 root root  4096 Aug  7  2012 cdrom
drwxr-xr-x  17 root root  4400 May 19 22:02 dev
drwxr-xr-x 173 root root 12288 May 19 22:02 etc
drwxr-xr-x   3 root root  4096 Aug  7  2012 home
lrwxrwxrwx   1 root root    32 May 19 10:30 initrd.img -> boot/initrd.img-3.8.0-22-generic
lrwxrwxrwx   1 root root    33 May 19 10:27 initrd.img.old -> /boot/initrd.img-3.8.0-22-generic
drwxr-xr-x  24 root root  4096 Apr 25 20:09 lib
drwxr-xr-x   2 root root  4096 Apr 25 18:54 lib64
lrwxrwxrwx   1 root root    36 Oct 27  2012 libnss3.so -> /usr/lib/x86_64-linux-gnu/libnss3.so
drwx------   2 root root 16384 Aug  7  2012 lost+found
drwxr-xr-x   3 root root  4096 Nov 11  2012 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   5 root root  4096 Mar 15 12:47 opt
dr-xr-xr-x 227 root root     0 May 19 22:01 proc
drwx------  17 root root  4096 Mar 27 20:25 root
drwxr-xr-x   2 root root  4096 Jan 29 11:51 .rpmdb
drwxr-xr-x  30 root root  1040 May 19 22:02 run
drwxr-xr-x   2 root root 12288 Apr 25 20:09 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   3 root root  4096 Aug 17  2012 srv
dr-xr-xr-x  13 root root     0 May 19 22:01 sys
drwxrwxrwt  12 root root  4096 May 19 22:19 tmp
drwxr-xr-x  10 root root  4096 Apr 25  2012 usr
drwxr-xr-x  15 root root  4096 May 19 10:32 var
lrwxrwxrwx   1 root root    29 May 19 10:30 vmlinuz -> boot/vmlinuz-3.8.0-22-generic
lrwxrwxrwx   1 root root    29 May 19 10:27 vmlinuz.old -> boot/vmlinuz-3.8.0-22-generic

---

### Post by jamesisin on 2013-05-19
I see many folders besides your /home folder.  What do you mean when you say you cannot see anything except your home folder?

What update did you run?  Did you upgrade from one version to another?

---

### Post by hoboy on 2013-05-19
> **jamesisin said:**
> I see many folders besides your /home folder.  What do you mean when you say you cannot see anything except your home folder?

What update did you run?  Did you upgrade from one version to another?

>I see many folders besides your /home folder. What do you mean when you say you cannot see anything except your home folder?

>What update did you run? Did you upgrade from one version to another? 

I just run Software update this morning, I have already upgraded from 12.04 to 13.04 without any problem untill now, and was fine before the update this morning.
On the Desktop on the left on Unity there is a Files Folder, before when I open this I could see all you can see on the console output, but now I an can only see 
Places/Recent
home
desktop
documents
downloads
music
pictures
videos
trash

---

### Post by jamesisin on 2013-05-19
Can you attach a screenshot of that?

---

### Post by hoboy on 2013-05-19
Here is the attachement

---

### Post by jamesisin on 2013-05-19
This looks normal to me.  I don't understand what's missing for you.  I see some files.  You are able to navigate to your Pictures directory.  What are you trying to accomplish and yet fail?

---

### Post by hoboy on 2013-05-19
> **jamesisin said:**
> This looks normal to me.  I don't understand what's missing for you.  I see some files.  You are able to navigate to your Pictures directory.  What are you trying to accomplish and yet fail?

I used to se 
/urs
/opt 

look here the full structure

[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)
they have despeared from the view since this morning
I am trying to get to the root structure in the files view I in the screenshot

---

### Post by jamesisin on 2013-05-19
Those would not normally appear in the left-hand pane.  You added those yourself at some point?  Can you just add them back?  They are both in the *ls* ouput you posted above.  You'll just need to recreate the shortcuts in the left-hand pane if you want them to appear there.

---

### Post by hoboy on 2013-05-19
> **jamesisin said:**
> Those would not normally appear in the left-hand pane.  You added those yourself at some point?  Can you just add them back?  They are both in the *ls* ouput you posted above.  You'll just need to recreate the shortcuts in the left-hand pane if you want them to appear there.

ooooooooook
Weird you said that, I have not done this specifically.
How do I do that ?
for example these 2 
drwxr-xr-x 10 root root 4096 Apr 25 2012 usr
drwxr-xr-x 15 root root 4096 May 19 10:32 var
I have absolutelly no idea how to do it

---

### Post by jamesisin on 2013-05-19
Navigate to the location in question.  Once there, you can drag and drop the folder into the left-hand pane.

To type in a location in Nautilus (the file browser you've been using) open any folder, use the Go menu, and select Location.  The two folders you want are /usr and /var respectively.

There are other ways but this should get you started.

---

### Post by hoboy on 2013-05-20
Is it this way you mean to navigated ??
luc@luc-Satellite-A300D:~$ cd /usr
luc@luc-Satellite-A300D:/usr$ nautilus
luc@luc-Satellite-A300D:/usr$ sudo nautilus
[sudo] password for luc: 

(nautilus:4146): IBUS-WARNING **: The owner of /home/luc/.config/ibus/bus is not root!

when I use nautilus it only open the home folder nothing else
------------------------------------------
How can I navigate to something I can not see ?
usr , var ... are not visible under files.

---

### Post by stinkeye on 2013-05-20
> **hoboy said:**
> Is it this way you mean to navigated ??
luc@luc-Satellite-A300D:~$ cd /usr
luc@luc-Satellite-A300D:/usr$ nautilus
luc@luc-Satellite-A300D:/usr$ sudo nautilus
[sudo] password for luc: 

(nautilus:4146): IBUS-WARNING **: The owner of /home/luc/.config/ibus/bus is not root!

when I use nautilus it only open the home folder nothing else
------------------------------------------
How can I navigate to something I can not see ?
usr , var ... are not visible under files.
He means goto the directory in nautilus and you can press ctrl+d to bookmark in the left pane.

The tree view option
[ATTACH=CONFIG]242802[/ATTACH] 
in the left pane has been removed.

Clicking on "Computer" in the left pane will show all your top directories.
[ATTACH=CONFIG]242803[/ATTACH]

---

### Post by hoboy on 2013-05-20
> **stinkeye said:**
> He means goto the directory in nautilus and you can press ctrl+d to bookmark in the left pane.

The tree view option
[ATTACH=CONFIG]242802[/ATTACH] 
in the left pane has been removed.

Clicking on "Computer" in the left pane will show all your top directories.
[ATTACH=CONFIG]242803[/ATTACH]
>He means goto the directory in nautilus and you can press ctrl+d to bookmark in the left pane.
I have send a screenshot can you please tell me where is Nautilus I should go to ?
I am not sure what Nautilus is here.

---

### Post by stinkeye on 2013-05-20
> **hoboy said:**
> >He means goto the directory in nautilus and you can press ctrl+d to bookmark in the left pane.
I have send a screenshot can you please tell me where is Nautilus I should go to ?
I am not sure what Nautilus is here.

Nautilus is the file browser.
So if there are particular folders you use a lot, browse to that location in the file browser and then hit ctrl+d to bookmark the folder.
As said before "Computer" in the left pane takes you to "/".

You cannot enable the old tree view in the left pane, just add individual bookmarks.

---

### Post by deadflowr on 2013-05-20
If you click the cog in the top right corner, there's an 'add bookmark' in there.

---

### Post by hoboy on 2013-05-20
> **deadflowr said:**
> If you click the cog in the top right corner, there's an 'add bookmark' in there.

Tks very much for all the help I got it.

---

