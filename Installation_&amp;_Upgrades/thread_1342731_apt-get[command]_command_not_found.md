---
title: "apt-get*[command]: command not found"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by genfly on 2009-12-01
Hi all,

I was fiddling around with terminal and must have wrecked something
I now keep getting error messages in terminal for example:

sudo apt-get update: command not found
sudo apt-get install vlc: command not found

However if i just type "apt-get" i get the normal output ie Usage: apt-get [options] command. But when i add a command it says not found!

If i type find / -iname "*apt-get*"
I get the response:
```

/usr/bin/apt-get
/usr/share/doc/auto-apt/examples/auto-apt-get-menu.sh
/usr/share/man/ja/man8/apt-get.8.gz
/usr/share/man/man8/apt-get.8.gz
/usr/share/man/es/man8/apt-get.8.gz
/usr/share/man/fr/man8/apt-get.8.gz
```

Any ideas please?!
Thanks in advance!

Best regards,
Genfly

---

### Post by genfly on 2009-12-01
P.S.*I*have*no*idea*why*its*adding*(stars)*between*every*word*i*wrote*in*this*thread.

---

### Post by StOoZ on 2009-12-01
what browser are you using?

---

### Post by genfly on 2009-12-01
google*chromium*4.0.260.0.*Gonna*try*firefox*now*

---

### Post by genfly on 2009-12-01
this*is*a*test

firefox*seems*to*do*the*same*thing.*I*might*revert*to*last*ubuntu's*release*if*i*cant*sort*these*2*things*out.*Its*100%*vital*for*me*to*fix*these*2*problems

ps.*when*im*on*facebook*it*doesnt*make*the*stars*but*instead*doesnt*add*spaces*whenever*i*post*a*message,*so*it*would*look*like*this:*hellomynameisgenfly

thanks*in*advance*for*any*help

PS.*i*did*a*clean*install*using*100%*of*my*hard*drive*on*my*asus*eeepc*s101

---

### Post by genfly on 2009-12-01
Fixed: Keyboard problem fixed by typing: ```
setxkbmap gb
``` in terminal. Still have the other problem though

---

### Post by oldos2er on 2009-12-01
You didn't change any permissions, did you? Maybe a look at your bash history to see exactly which commands were run would help.

---

### Post by genfly on 2009-12-02
I found the code i used in terminal. Could this have ruined something? if so how do i fix it please

```
sudo killall apt-get
sudo rm /var/lib/dpkg/lock
```

thanks*and*regards

---

### Post by genfly on 2009-12-02
Fixed?

I used the ```
setxkbmap gb
``` command again because last post came out with *stars* again and terminal seems to be working fine now for all commands. Now I just gotta find a way to auto run setxkbmap gb command at startup and i think i know how. 

**In summary it looks like it was a wrongly set keyboard mode caused commands in terminal not to work. As long as i get the code ```
setxkbmap gb
``` to autorun at startup, all works.**


Thanks everyone, this problem seems to be solved

---

### Post by ConstintineVamp on 2009-12-02
Omg lol thts a fun issue lol

---

