---
title: "TinyOS  Vs  Ubuntu  10.10"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by ccsi on 2011-02-09
good evening every one ....


i am a little beginner in Ubuntu and i am working on TinyOS ,

And i want to ask you if are  there any compatible TinyOS with Ubuntu  10.10???!

I   found compatible one with  Ubuntu 9.10 & 8.10 but I do not  Know if it could compatible with 10.10???

please help me  

:confused:

---

### Post by Kirboosy on 2011-02-09
Welcome to the forums!! :)

Well even though somethings aren't "made" for lucid it will still work oftentimes. You never know until you try. 

If it does have any errors please post them.

[http://docs.tinyos.net/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages](http://docs.tinyos.net/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages)

---

### Post by ccsi on 2011-02-09
thank you 
:)

but I found this 
ubuntu@ubuntu-MM061:~$  sudo apt-get install tinyos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Unable to locate package tinyos[/COLOR]


after : sudo apt-get install tinyos   command 

Note: I did not  do  first command : 1) Remove any old tinyos repository from /etc/apt/sources.list and add the following: 
  Supported distributions are (edgy, feisty, gutsy, hardy, jaunty, karmic, lucid)

because I do not have TinyOs before

---

### Post by Kirboosy on 2011-02-09
Run this command in your terminal

```
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main
```

I know you are using Maverick but it should still work.

---

### Post by ccsi on 2011-02-10
12 hour  left  in order to find  solution for that error

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found

when i tried running previous command :(   

can you help me  please ?!

---

### Post by Kirboosy on 2011-02-10
Oh I'm sorry. I wasn't thinking clearly when I posted that...

Navigate to System-->Admin-->Software Sources

Then click the Other "Software Tab"

Hit the "Add" button and paste ```

deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main
```

---

### Post by ccsi on 2011-02-10
thanx

but  ...:oops:


I did not find  " Software source"  in Administration  !!

I know that I bother you  :oops:

---

### Post by Kirboosy on 2011-02-10
Are you using [Gnome]("http://www.gnome.org/") as your default Window Manager?


Ok lets try this...

Run this command in a Terminal
```
sudo add-apt-repository ppa:deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main
```Then run
```
sudo apt-get update
```then...
```
sudo apt-get install tinyos
```You aren't a bother, we all started as beginners at one point in time. :smile:

---

### Post by ccsi on 2011-02-10
I use  Ubuntu as an independent OS  not as partition on C:/  or D:/
" i did not understand what dose you mean by  "  GNOME"  and how I Know
why ? is there wrong in my OS  since there is no Software sources ?? 

any way i tried your command i found this message 

Error: need a repository as argument  

?! 

I hope that i find  worked solution because i spent a lot of time without result ....but still i have a hope since you guide me :)

---

### Post by Kirboosy on 2011-02-10
Gnome is the interface. The look of Ubuntu... Does your screen (for the most part) look like [this?]("https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources.png")

---

### Post by ccsi on 2011-02-10
yes it is 

but no such icon !!!

---

### Post by ccsi on 2011-02-10
i found that :

[http://docs.tinyos.net/index.php/Getting_started_using_Ubuntu_9.10_and_TelosB_motes](http://docs.tinyos.net/index.php/Getting_started_using_Ubuntu_9.10_and_TelosB_motes)

what do you think  ?
i found how to open that file and add dep......etc  command but i put your command rather  :

deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) hardy mainam I on the right  side  ?

note:  I choose tinyos 2.1.1  ..

also i faced  a window about java6-jer  ..... but i could not  press OK !!!!

---

### Post by Kirboosy on 2011-02-10
Do you have __[java]("http://www.java.com/") installed on the computer? If not I can walk you through that as well. :)

---

### Post by uRock on 2011-02-10
Software sources is not in System> Administration by default in 10.10. You have to go to Applications> Ubuntu Software Center, then click Edit and select Software Sources.

---

### Post by ccsi on 2011-02-10
> **Caboose885 said:**
> Do you have [java]("http://www.java.com/") installed on the computer? If not I can walk you through that as well. :)


I think i do not have java i will install it ,,,

and  i will keep following you ...

---

### Post by ccsi on 2011-02-10
> **uRock said:**
> Software sources is not in System> Administration by default in 10.10. You have to go to Applications> Ubuntu Software Center, then click Edit and select Software Sources.


got it 

thank you so much :)

---

### Post by ccsi on 2011-02-10
[COLOR=Black][Caboose885  ]("http://ubuntuforums.org/member.php?u=900617")

do you prefer  to start from that step 

" software sources" ?

>> after [/COLOR][[COLOR=#D40000]**uRock**[/COLOR]]("http://ubuntuforums.org/member.php?u=1018339")  told me how to find it

---

### Post by ccsi on 2011-02-10
finally i disabled the faced problem >>are there any command that tell me if TinyOS installed correctly > still Iam not sure :oops:

but when i started  the tutorial in this page 

[http://docs.tinyos.net/index.php/Getting_Started_with_TinyOS](http://docs.tinyos.net/index.php/Getting_Started_with_TinyOS)

after 
 tos-check-env


i found a lot of warning that asked to update  is it OK to ignore them  ?

  if not, how do i update them  ?

---

### Post by Kirboosy on 2011-02-10
Well just open up the software sources and add it like I instructed you before...

Click the Other "Software Tab"

Hit the "Add" button and paste

```
deb http://tinyos.stanford.edu/tinyos/dists/ubuntu lucid main
```


Then run
```
sudo apt-get update
```
then...
```
sudo apt-get install tinyos
```

---

### Post by ccsi on 2011-02-11
^^
I got this statement in my terminal : [COLOR=Red]Setting up for TinyOS 2.1.1[/COLOR]

at the top , I think  Tinyos is installed correctly   , is not it ?
-----------
thank you so much my friend you give me help full guide you are the best  ,I will not hesitate to ask your opinion when i need .

your site totally help me and i will be Active member just like you.

---

### Post by Kirboosy on 2011-02-11
Yes! I would say that everything installed correctly! :D

Glad to help. I used to have very few beans until I decided to start helping out the community. I hope you enjoy using Ubuntu. :)


Now if you would mark the thread as solved that would be great. (Under Thread Tools)

---

### Post by ccsi on 2011-02-11
done .....

:)

---

### Post by Damien_74 on 2011-02-12
Caboose and ccsi,

I followed all your advice and i am still stuck at the installation of tinyos...

I installed and update java6 then i try to add these many line in the Sources.liste :

deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) <distribution> main
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main
deb-src [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main
[SIZE=1]deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) <ubuntu_release> main

And executed the command :

sudo apt-get install tinyos-2.1.1
sudo apt-get install tinyos

I always get this error (cf end)

[COLOR=Red]**Oups by trying again to get the error it works! Crazy story... **[/COLOR]
I let this post to give hope for people how try like all the option, at the end it could work xD

Anyway thank you for all the advices I learn some new tips on ubuntu!

Cheers,

Damien

Error in the console :
E: Unable to locate package tinyos



error in the software source :

[/SIZE][SIZE=1][I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: NODATA 2

W: Failed to fetch http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/<distribution>/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/lucid/main/source/Sources.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release](http://id.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I][/SIZE]

---

### Post by ccsi on 2011-02-12
well,

first of all you have to know that the problems faced you may no body else had faced, and it  is OK 
also may the proposed  solutions that worked with some one not work with you , and also it is OK.

but try to follow this 

[http://docs.tinyos.net/index.php/Getting_started_using_Ubuntu_9.10_and_TelosB_motes](http://docs.tinyos.net/index.php/Getting_started_using_Ubuntu_9.10_and_TelosB_motes)

with what Mr. Caboose  support us with  

for every error faced, try to search on google and it will help.

I am still beginner , but i will help you as possible i can , also the other here will

tell us what will happen with you :)

---

### Post by Kirboosy on 2011-02-13
Remove all of the other repositories you added except for this one

```
deb http://tinyos.stanford.edu/tinyos/dists/ubuntu lucid main
```

then run in the terminal ```
sudo apt-get update
```

then run ```
sudo apt-get install tinyos
```

---

### Post by rioubun on 2011-02-24
Hello,

I have just started with Ubuntu (10.10). I have been trying to install tinyOS, but getting this error "Unable to locate TinyOS"

I looked into the replies on this, and tried all the possible solutions but still getting the same problem.

any workaround possible?

---

### Post by ccsi on 2011-02-26
I hope any one else can help you even though I tired and tried many many solutions with no result , I finally found here the solution... do not give up ... there will be here some one can help you :)

---

### Post by deceaseddolphin on 2011-03-09
> **rioubun said:**
> Hello,

I have just started with Ubuntu (10.10). I have been trying to install tinyOS, but getting this error "Unable to locate TinyOS"

I looked into the replies on this, and tried all the possible solutions but still getting the same problem.

any workaround possible?
open synaptic manager and type 'tinyos'. you'll find a list of files.

select tinyos-2.1.1 (which automatically select other bunch of files) and mark for installation.

that should work.

---

