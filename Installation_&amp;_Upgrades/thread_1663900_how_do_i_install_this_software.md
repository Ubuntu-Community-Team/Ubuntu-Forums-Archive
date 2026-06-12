---
title: "how do i install this software"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by suryak on 2011-01-10
How do i install my modem software in ubuntu .. 
The following text is the ' read me ' file given ..
give me the detailed way to do it.. 
> there are totally 6 file in the directory from where the software has to be installed 
 1. data.bin 2. DataCard_Verify 3. install 4.MobilePartner.tar.gz 5. readme.txt 6. SysConfig.dat 
and the directory location in which these are present is [PHP]/media/Idea Net Setter /Linux[/PHP][PHP]--How to Install---------------------- 
*You need login as root* 
1. Run "install" in TERMINAL to install MobilePartner 
   eg: # bash /<path>/install 
    
2. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit. 
 
3. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct 
 
4. Finish installing 
 
--How to run-------------------------- 
* From shortcut in desktop 
 
* Run MobilePartner in your install path 
   eg: # /<install path>/MobilePartner 
 
* Plug in your device, it will run automatically(Not supported in Xandros)[/PHP]

---

### Post by suryak on 2011-01-10
they aren't php codes !!

---

### Post by pricetech on 2011-01-10
It looks like the readme pretty well covers it, but if you could give us more information on the modem it might be helpful.

---

### Post by suryak on 2011-01-11
Its a USB HSPDA, Modem, given In build software to install.

---

### Post by matt_symes on 2011-01-11
Hi

What have you tried to do so far to install it?

Kind regards

---

### Post by suryak on 2011-01-12
I don't remember exactly but.. what I did is .. 
logged in as root by entering ' sudo su'
and [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#FF8000]# bash /<path>/install .. 

[/COLOR][/COLOR]

---

### Post by matt_symes on 2011-01-12
Hi

So you did...

```
sudo su
/media/Idea\ Net\ Setter\ /Linux 
```

escaping the spaces? What error messages did you get? Post them back here.

Kind regards

---

### Post by suryak on 2011-01-12
I did like this :
/media/IdeaNetSetter/Linux/install .. 
I'll try the way you said.. and post again..

---

### Post by matt_symes on 2011-01-12
Hi

I'm a bit confused. You are not giving us enough information to help you.

What exactly is the path to the install file? What exactly have you typed to try to install it?

Try to install and post the result back here including all the errors.
You need to help us before we can help you ;)

I took 

```
/media/Idea\ Net\ Setter\ /Linux
```

from 

```
/media/Idea Net Setter /Linux
``` 

in your first post. I assumed that was the path to the install file.

Kind regards

---

### Post by suryak on 2011-01-12
> /media/Idea Net Setter /Linux: /media/Idea Net Setter /Linux: is a directory
bash: /media/Idea: No such file or directory
  This is what I got the message when I entered the code you have give.. in the root.

Actually I already mentioned in my first question.. 
> /media/Idea Net Setter /Linux In this directory there are below mentioned files.
1. data.bin
2.DataCard_Verify
3.install
4.MobilePartner.tar.gz
5.readme.txt
6.SysConfig.dat

These are the directory details .. 

and The below things are the attempts I did in terminal via root ( logged in from sudo su)
> bash /media/IdeaNetSetter/Linux/install -- and there is no answer.

so I did this way in the terminal.. 
> ls /mediain this there are these options ' cdrom  cdrom0  floppy  floppy0  IdeaNetSetter  Idea Net Setter '.. so here i selected 'Idea Net Setter'.. by entering
> Idea Net Setter and the answer is " Idea: Command not found.
Then I selected > IdeaNetSetter then the answer is IdeaNetSetter: Command Not found. 

I'm not understanding anything.. 

If you don't understand what I'm trying to say.. follow my first question and read the ' read me ' file i've given.. and tell me how to do ..

---

### Post by matt_symes on 2011-01-12
Hi

Try this.

```

sudo su
bash "/media/Idea Net Setter /Linux/install"

```

If that gives problems try

```

sudo su
bash "/media/Idea Net Setter/Linux/install"

```

Notice no space between Setter and Linux (Setter/Linux) in the second one.

Kind regards

---

