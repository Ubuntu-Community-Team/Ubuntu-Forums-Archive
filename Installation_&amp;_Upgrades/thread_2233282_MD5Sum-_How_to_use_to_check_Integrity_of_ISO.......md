---
title: "MD5Sum- How to use to check Integrity of ISO......"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by Caleb012 on 2014-07-07
I need very easy to follow instruction regarding checking the integrity of a Ubuntu 14 download. These instructions need to be simple enough for someone with very limited computer ability, especially as pertaining to Linux. Thank you very much for any assistance in this matter!

---

### Post by Bashing-om on 2014-07-07
Caleb012; Hi !

Checking the .iso is vital, and simple.
My method:
I have my browser set to download files by default ( the default setting) to the /Downloads directory in my /home, so the command:
```

md5sum ~/Downloads/ubuntu-12.04.1-desktop-amd64.iso

``` will generate a value for "that" file - your file be be a different one -.
On the site where you downloaded the .iso is the hash value that should match exactly what the md5sum command returned.
In detail:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[INDENT][INDENT]Hope This Helps
[/INDENT][/INDENT]

---

### Post by Caleb012 on 2014-07-07
Thank you so very much for using your knowledge regarding Ubuntu to help others! I open Terminal and type in the info you provided but I get "No such file or directory". I apologize for my lack of knowledge......

---

### Post by sammiev on 2014-07-07
Hope [this]("https://help.ubuntu.com/community/HowToMD5SUM") will help you a little more.

---

### Post by Bashing-om on 2014-07-07
Caleb012; Hey !

Not a problem, none of us were born knowing what we know. Time and effort fixes that !

OK, to the issue at hand. 
Where did you download the file to ?
Let's look and see if it is in fact in the /Downloads directory, and what the name of the file is.
Post back the output - between code tags - of terminal command:
```

ls -la ~/Downloads

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
FYI:  '~/' is shorthand for the path  /home/Your_User_Name_here/
Such that my former example expands to:  '/home/sysop/Downloads/ubuntu-12.04.1-desktop-amd64.iso' where 'sysop' is my User_Name.

[INDENT][INDENT]all in the process
[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Caleb012 on 2014-07-07
Thank you very much. I normally use the sudo command when using the terminal. Could you point me in the direction I need to go when I use that link? Thanks again!

---

### Post by Bashing-om on 2014-07-07
Caleb012; Sure !

1stly, never use sudo unless it is required to gain the elevated privileges of the administrative level. In this case it is not needed and using 'sudo' in this instance could have very undesirable side effects. Again the process of learning .. elevated privileges are not required for operating within your own /home.

To follow a link within the post: right click on it and in the resulting context box choose " open in a new tab"  which will give you a new tab in your browser ( top bar) .. click on that new tab.

once you know how
[INDENT][INDENT]easy as falling out of bed wide awake
[/INDENT][/INDENT]

---

### Post by Caleb012 on 2014-07-07
jaye@jaye-Inspiron-1501:~$ md5sum ~/Downloads/ubuntu-12.04.1-desktop-amd64.iso
md5sum: /home/jaye/Downloads/ubuntu-12.04.1-desktop-amd64.iso: No such file or directory
jaye@jaye-Inspiron-1501:~$ ls -la ~/Downloads
total 999112
drwxr-xr-x  6 jaye jaye       4096 Jul  7 14:55 .
drwxr-xr-x 35 jaye jaye       4096 Jul  7 07:53 ..
drwxr-xr-x  2 jaye jaye       4096 Jul  4 09:38 12.04 - Can I make Ubuntu boot from a SD card? - Ask Ubuntu_files
-rw-rw-r--  1 jaye jaye      80142 Jul  4 09:38 12.04 - Can I make Ubuntu boot from a SD card? - Ask Ubuntu.html
-rw-rw-r--  1 jaye jaye    2890025 Jun 18 17:40 Bitdefender_TS_2014_UserGuide_en.pdf
-rw-rw-r--  1 jaye jaye    2919149 Jun 14 07:41 John Deere Manual.pdf
drwxrwxr-x  2 jaye jaye       4096 Jul  4 08:01 Linux Command Line
-rw-r--r--  1 jaye jaye      49152 Jul  7 14:55 md5sum.exe
-rw-r--r--  1 jaye jaye 1017118720 Jul  4 09:30 ubuntu-14.04-desktop-i386.iso
drwxrwxr-x  3 jaye jaye       4096 Jul  4 07:59 Ubuntu from SD Card
drwxrwxr-x  3 jaye jaye       4096 Jul  4 08:00 Windows 7 Tips
jaye@jaye-Inspiron-1501:~$ 


I think the download is indeed in the Download Folder........

---

### Post by Bashing-om on 2014-07-07
Caleb012; Yeah, 

It is, it is present in the /Downloads directory.
Make the terminal command as:
```

md5sum ~/Downloads/ubuntu-14.04-desktop-i386.iso

```
When it gets done calculating will give you the hash value ( and the path/filename from which it was generated) .. all we care about presently is the value ( for example: dccff28314d9ae4ed262cfc6f35e5153. which is for a 64 bit .iso file).
Now compare that value from that of the value posted from where you downloaded 'ubuntu-14.04-desktop-i386.iso' from.
--------------
jaye, learn to use "code tags" it can be important to do so in this forum .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Caleb012 on 2014-07-07
I certainly apologize for my ignorance........I typed ```
 ls -la ~/Downloads 
``` in the terminal to no avail.....got invalid command or something like that......

---

### Post by Bashing-om on 2014-07-07
Caleb012; HUmm..
that "ls -la ~/Downloads" is a valid command. { hey, I just tested and verified it is valid as is}
Let's do it like so: our only present goal is to obtain that hash value:
```

cd
md5sum ~/Downloads/ubuntu-14.04-desktop-i386.iso

```
the 'cd' command to make sure you are in your /home directory as your "Present Working Directory" - PWD-  such that the system sees /Downloads.

What now ?

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Caleb012 on 2014-07-07
As being new to Linux.........Code Tags are completely new to me........

---

### Post by sotiris2 on 2014-07-07
May I remind that there is also the alternative of typing 
```
md5sum
```
and then click and drag the file from a nautilus (files) window to the terminal? This will autocomplete the path.

---

### Post by Caleb012 on 2014-07-07
Thanks to all for their kindness in assisting me. "Code Tags" are completely new to me and will require that I "study up" on them. My procedure is to normally enter whatever in the terminal.....I have not used anything there save to type away......Thank you for your patience! You guys are terrific in how you help newcomers! I am very proud to now be a user of Ubuntu 14! I love it!

I finally got it to work and my download was successful and checked out to be accurate!

---

### Post by lisati on 2014-07-07
> **Caleb012 said:**
> Thanks to all for their kindness in assisting me. "Code Tags" are completely new to me and will require that I "study up" on them. My procedure is to normally enter whatever in the terminal.....I have not used anything there save to type away......Thank you for your patience! You guys are terrific in how you help newcomers! I am very proud to now be a user of Ubuntu 14! I love it!

I finally got it to work and my download was successful and checked out to be accurate!

"Code tags" are something that people use on forums such as this one to help make sure that what they type gets formatted properly. The general idea is that you put [noparse]```
 at the start of what you're copying to the forum, and 
```[/noparse] at the end. You wouldn't normally type them in on the terminal.

Some more examples can be found [here]("http://ubuntuforums.org/misc.php?do=bbcode").

---

### Post by Bashing-om on 2014-07-07
Caleb012; Outstanding !

See, you do do good work.
As this matter is now concluded - I hope to your satisfaction - ;
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
The tutorial:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you 'buntu'n
[/INDENT][/INDENT]

---

