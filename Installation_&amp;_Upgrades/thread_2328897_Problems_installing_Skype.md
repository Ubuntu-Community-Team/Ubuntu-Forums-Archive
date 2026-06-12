---
title: "Problems installing Skype"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by leiss on 2016-06-25
I saw some youtube installing skype but i encountered a problem 
it gets me this fail message
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/no.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages

How do i fix it?

---

### Post by ajgreeny on 2016-06-25
Tell us more about how you tried to install skype and the hardware you are trying to install it to.

Is it 32 or 64 bit?
Have you enabled the canonical-partners repos where you will find skype and can install in the usual way?

---

### Post by RobGoss on 2016-06-25
Hello and welcome to the forum, What version of Ubuntu are you using? I also believe with some distributions **Skype** can be installed from the Software center I know with** Ubuntu Mate 16.04** it's available but I think with **Ubuntu 16.04** it cannot be installed from the Ubuntu Software center

Try running this command and completely remove Skype

```
 [COLOR=#111111][FONT=Consolas]sudo apt-get purge skype[/FONT][/COLOR]
```

Then follow the instruction here in this post to reinstall Skype on your system
[http://askubuntu.com/questions/488053/how-to-install-skype-4-3/488062#488062](http://askubuntu.com/questions/488053/how-to-install-skype-4-3/488062#488062)

---

### Post by ajgreeny on 2016-06-25
> **RobGoss said:**
> Hello and welcome to the forum, What version of Ubuntu are you using? I also believe with some distributions **Skype** can be installed from the Software center I know with** Ubuntu Mate 16.04** it's available but I think with **Ubuntu 16.04** it cannot be installed from the Ubuntu Software center

Try running this command and completely remove Skype

```
 [COLOR=#111111][FONT=Consolas]sudo apt-get purge skype[/FONT][/COLOR]
```

Then follow the instruction here in this post to reinstall Skype on your system
[http://askubuntu.com/questions/488053/how-to-install-skype-4-3/488062#488062](http://askubuntu.com/questions/488053/how-to-install-skype-4-3/488062#488062)
I've never used the ubuntu software-centre nor the new ubuntu-software, or whatever it's called; I use synaptic if I use a GUI at all, but skype can certainly be installed from repos.

I have just done it and used it successfully so no problem should be seen if you try, so long as you have the partner repos enabled.

---

### Post by RobGoss on 2016-06-25
> [COLOR=#000000]I've never used the ubuntu software-centre nor the new ubuntu-software, or whatever it's called; I use synaptic if I use a GUI at all, but skype can certainly be installed from repos.[/COLOR]

[COLOR=#000000]I have just done it and used it successfully so no problem should be seen if you try, so long as you have the partner repos enabled.[/COLOR]

Thanks for sharing a better of installing Skype seems to be quicker and on point I'll have to start using **synaptic** more often I was wondering about **_partner repos enabled _**but I understand know [http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository](http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository)

---

