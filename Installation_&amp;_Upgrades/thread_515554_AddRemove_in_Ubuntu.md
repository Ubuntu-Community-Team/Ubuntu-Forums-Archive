---
title: "Add/Remove in Ubuntu"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by Chriseverclear on 2007-08-02
Hello,

I am a completely newbie to Ubuntu.

I am just wondering. What is the best way to add or remove programs.
In Windows, it is basically control panel-->add and remove.

I have been installing several programs for ubuntu, but some of the programs are not useful to me.

I am looking for a way in terminal where i can view all the programs that i have and how to remove them.

Can someone tell me if there's a good guide i can look or a few commands.

i have searched the forums but i couldn't any answer for this.

thanks.

---

### Post by Claus7 on 2007-08-02
Hello,

go to System->Administration->Synaptic Package Manager, give your password and there you should see the programs that you have installed or you want to install.

Except from that there is also automatix :
[http://www.getautomatix.com/](http://www.getautomatix.com/)

which will help you mostly on installing some codecs and other useful things. Have in mind that you will open only one of the aforementioned programs at a time. 

Even though these will cover most of your needs you might need also to install some programs yourself, because they simply do not exist in the list of the programs in question.

Regards!

---

### Post by Chriseverclear on 2007-08-02
Hey thanks.

---

### Post by Chriseverclear on 2007-08-03
Is there a way to do this in terminal?

---

### Post by mcduck on 2007-08-03
> **Chriseverclear said:**
> Is there a way to do this in terminal?

sure, run 'aptitude' in a terminal and you'll get a CLI version of what Synaptic does.

---

### Post by ike on 2007-08-03
> **mcduck said:**
> sure, run 'aptitude' in a terminal and you'll get a CLI version of what Synaptic does.

or you can use apt-get.

usage:

install package "xyz":
```
sudo apt-get install xyz
```

remove package "xyz":
```
sudo apt-get remove xyz
```

search for packages:
```
sudo apt-cache search xyz
```

see manpages for apt-get for more info (run "man apt-get" in a terminal).

---

### Post by mcduck on 2007-08-03
Yeah, i prefer apt-get too, but it's easier to browse repositories and list packages in command line with aptitude than apt-get, as aptitude has ncurses-based CLI interface. Just run 'sudo aptitude' to open it. ;)

---

### Post by ike on 2007-08-03
> **mcduck said:**
> Yeah, i prefer apt-get too, but it's easier to browse repositories and list packages in command line with aptitude than apt-get, as aptitude has ncurses-based CLI interface. Just run 'sudo aptitude' to open it. ;)

Yeah I know, just wanted to make sure Chriseverclear was aware of all the options :)

---

### Post by mcduck on 2007-08-04
> **ike said:**
> Yeah I know, just wanted to make sure Chriseverclear was aware of all the options :)

Sure. In that case I have to mention the Add /Remove.. under Applications menu. As long as the program to be installed is available there, I can hardly imagine easier way to install and remove software :)

---

