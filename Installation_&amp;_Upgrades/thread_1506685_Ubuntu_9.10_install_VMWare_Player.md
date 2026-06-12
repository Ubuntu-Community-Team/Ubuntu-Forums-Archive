---
title: "Ubuntu 9.10 install VMWare Player"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by felixvah on 2010-06-10
I ran into a problem and I can't find any thing on the web to help me.  Can someone help me please?  I've tried to install VMware player 3.xx into Ubuntu 9.10 and this what happen to me:

sudo chmod +x VMware-Player-3.0.0-203739.i386.bundle
sudo bash ./VMware-Player-3.0.0-203739.i386.bundle

here's the error which I don't know where to look for:

./VMware-Player-3.0.0-203739.i386.bundle: line 110: syntax error near unexpected token `newline'
./VMware-Player-3.0.0-203739.i386.bundle: line 110: `<html>

please post or direct me to a link if you know the answer.  Thank you

---

### Post by dabl on 2010-06-10
I have not found that the downloaded .bundle file even needs the permissions changed on it.  I just copy the download to my /tmp directory:

/tmp$ sudo cp /home/dabl/Downloads/VM{tab-to-complete} .

(Don't omit the period at the end of the command).

then I run it:

/tmp$ sudo sh VM{tab-to-complete} and it runs correctly.

Try it. :wink:

---

### Post by felixvah on 2010-06-10
> **dabl said:**
> I have not found that the downloaded .bundle file even needs the permissions changed on it.  I just copy the download to my /tmp directory:

/tmp$ sudo cp /home/dabl/Downloads/VM{tab-to-complete} .

(Don't omit the period at the end of the command).

then I run it:

/tmp$ sudo sh VM{tab-to-complete} and it runs correctly.

Try it. :wink:

I'm sorry, but what do you mean by VM{tab-to-complete}  Can you please explain that to me.  I'm new and not quite understand..

---

### Post by zakcobb on 2010-06-11
tab auto completes the command.

---

### Post by felixvah on 2010-06-11
> **zakcobb said:**
> tab auto completes the command.

I don't know if I understand you correctly, but this is what I got:

fwvang@lenovo:~$ /tmp$ sudo cp VMware-Player-3.1.0-261024.i386.bundle{tab-to-complete}.
bash: /tmp$: No such file or directory
fwvang@lenovo:~$ 

I've tried VM{tab-to-complete}. as well but it didn't work..

I don't know if I follow you correctly.

Can you advise if I done it correctly?

Thanks..

---

### Post by steamdog on 2010-06-11
Hi Felixvah

Looks like we are both getting the same error when trying to install VMWare player 3.1.0 on Ubuntu 9.10.   

After logging in to the terminal and changing directory to the folder containing the VM player bundle file, I used the following command: 

[B]sudo sh VMware-Player-3.1.0-261024.i386.bundle
[/B]
It then prompts me for the password:
**[sudo] password for administrator: **

**It then returns the error:**
VMware-Player-3.1.0-261024.i386.bundle: 110: Syntax error: newline unexpected
administrator@ubuntu:~/Documents/gnb1$ 

I'm new to Ubuntu as well so either we are both doing something wrong or the or VM player won't run on Ubuntu 9.10. ?

Anybody any ideas....?

---

### Post by felixvah on 2010-06-11
> **steamdog said:**
> Hi Felixvah

Looks like we are both getting the same error when trying to install VMWare player 3.1.0 on Ubuntu 9.10.   

After logging in to the terminal and changing directory to the folder containing the VM player bundle file, I used the following command: 

[B]sudo sh VMware-Player-3.1.0-261024.i386.bundle
[/B]
It then prompts me for the password:
**[sudo] password for administrator: **

**It then returns the error:**
VMware-Player-3.1.0-261024.i386.bundle: 110: Syntax error: newline unexpected
administrator@ubuntu:~/Documents/gnb1$ 

I'm new to Ubuntu as well so either we are both doing something wrong or the or VM player won't run on Ubuntu 9.10. ?

Anybody any ideas....?

That's exactly what I get.  I followed the instruction above but I'm going no where.  If you figured it out, please let me know.

Thanks for you post!

---

### Post by dabl on 2010-06-15
There is a function of the bash shell called "bash completion":

[http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1](http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1)

So, when I wrote that you should type "... VM{tab-to-complete]" I meant that you would type only the first two letters of the target file name, and then press the Tab key on your keyboard, and let it finish the filename for you.  :)

---

### Post by felixvah on 2010-06-15
> **dabl said:**
> There is a function of the bash shell called "bash completion":

[http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1](http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1)

So, when I wrote that you should type "... VM{tab-to-complete]" I meant that you would type only the first two letters of the target file name, and then press the Tab key on your keyboard, and let it finish the filename for you.  :)

thanks, but it didn't work for me.  Here's what I've got:
fwvang@lenovo:~$ sudo sh /tmp/VMware-Player-3.1.0-261024.i386.bundle
/tmp/VMware-Player-3.1.0-261024.i386.bundle: line 110: syntax error near unexpected token `newline'

---

### Post by juhvu on 2010-06-21
Hello,

had the same problem with my 10.04 (newline 100 unexpected). The reason was that the download I tried to 'sudo sh' i.e. install was actually a HTML snippet, not the real bundle.

It seems that using the download manager on the vmware site causes this (well dunno what really causes it, on my Chrome that's the result anyway). Choosing the Download Manually gives the right bundle, which is significantly bigger (98 Mb).

Hope you get it working.

---

### Post by 130s on 2010-11-22
> **juhvu said:**
> Hello,

had the same problem with my 10.04 (newline 100 unexpected). The reason was that the download I tried to 'sudo sh' i.e. install was actually a HTML snippet, not the real bundle.

It seems that using the download manager on the vmware site causes this (well dunno what really causes it, on my Chrome that's the result anyway). Choosing the Download Manually gives the right bundle, which is significantly bigger (98 Mb).


Same problem occurred in my environment, and juhvu's suggestion worked for me. Thanks! :D

---

### Post by k50aker on 2011-02-07
> **juhvu said:**
> Hello,

had the same problem with my 10.04 (newline 100 unexpected). The reason was that the download I tried to 'sudo sh' i.e. install was actually a HTML snippet, not the real bundle.

It seems that using the download manager on the vmware site causes this (well dunno what really causes it, on my Chrome that's the result anyway). Choosing the Download Manually gives the right bundle, which is significantly bigger (98 Mb).

Hope you get it working.

Thanks A million!! It worked for me on Ubuntu 10.10.

---

### Post by ExaltMGNJCTM on 2011-07-13
I had the same problem while using Ubuntu 11.04, Firefox browser.  I re-downloaded using the VMware Download Option "Use Web Browser" and then the install was successful.

---

