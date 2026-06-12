---
title: "rpm to deb"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by taxi16 on 2007-06-11
hi,can anybody tell me where i am going wrong ?i am trying to convert this aver media rpm to deb file so i can install it on ubuntu 7.04.i am very new to linux and would be glad of any help,i have taken a screen shot of the terminal plus one of the filefile.file:///home/philip/Desktop/Screenshot-philip%40philip-laptop%3A%20~.png
file:///home/philip/Desktop/Screenshot-philip%40philip-laptop%3A%20~.png
:(

---

### Post by merlinus on 2007-06-11
Use alien, available via synaptic.

-merlin

---

### Post by dfreer on 2007-06-11
You'll have to attach those screenshots, they are currently not showing up correctly. Beyond that, what command are you typing to convert the RPM's to DEB's?

---

### Post by taxi16 on 2007-06-11
[http://ubuntuforums.org/images/uf/attach/png.gifhttp://ubuntuforums.org/images/uf/attach/png.gif](http://ubuntuforums.org/images/uf/attach/png.gifhttp://ubuntuforums.org/images/uf/attach/png.gif)

---

### Post by stchman on 2007-06-11
> **taxi16 said:**
> hi,can anybody tell me where i am going wrong ?i am trying to convert this aver media rpm to deb file so i can install it on ubuntu 7.04.i am very new to linux and would be glad of any help,i have taken a screen shot of the terminal plus one of the filefile.file:///home/philip/Desktop/Screenshot-philip%40philip-laptop%3A%20~.png
file:///home/philip/Desktop/Screenshot-philip%40philip-laptop%3A%20~.png
:(

First install alien:

sudo apt-get -y install alien

You can now convert the package to a .deb by doing the following.  Say for example you are converting widget.rpm to widget.deb

sudo alien --scripts --keep-version -d ./widget.rpm

This will convert the .rpm to a .deb.

Make sure you put the path, that is why I used the ./ in front of the filename.

You can then install the package by doing the following:

sudo dpkg -i widget.deb

---

### Post by dfreer on 2007-06-11
Actually, your current problem is you have incorrect syntax:
this is what you are currently doing:
```
sudo alien -d yourfile.rpm
```

What you need to do is this command:
```
sudo alien -d *the_folder_that_holds_the_file*/yourfile.rpm
```

---

### Post by Lord Illidan on 2007-06-11
Also, know that the shell has text completion. So you can type in the first few letters of the word, and it will complete them itself, if you press TAB. This way you can easily type in long commands.

---

### Post by taxi16 on 2007-06-11
file:///home/philip/Desktop/Screenshot.png
ihave taken a screen shot i am not sure how i attached the last ones ,but this is how i put the location ofthe file ,
     sudo alien -d home_philip_Desktop /AVerMedia-MTSA-FC4-0.35Beta-1.i386.rpm
i am also try to attach this file:///home/philip/Desktop/Screenshot.png.tar.gz
my problam is that i have only just installed linux on my laptop even though i ihave been thinking about it for 1 year!! iwould hope this explains my ignorance
.[http://ubuntuforums.org/images/uf/attach/png.gif](http://ubuntuforums.org/images/uf/attach/png.gif). i hope this is the screen shot

---

### Post by taxi16 on 2007-06-11
sorry that is the wrong screen sho ihope this is the right  one
[http://ubuntuforums.org/images/uf/attach/png.gif](http://ubuntuforums.org/images/uf/attach/png.gif)

---

### Post by stchman on 2007-06-11
> **taxi16 said:**
> sorry that is the wrong screen sho ihope this is the right  one
[http://ubuntuforums.org/images/uf/attach/png.gif](http://ubuntuforums.org/images/uf/attach/png.gif)

Give us a pwd.

It looks like you forgot the / in front of your home statement.  Here is the correct syntax I believe:

sudo alien -d /home/philip/Desktop/AverMedia-MTSA-FC4-0.35Beta-1.i386.rpm

---

### Post by peppy.ch on 2007-06-11
hi

I can see on your screen shot that you type in "home_philip_........" for the path. this is not a valid path trey with the following command:

sudo alien -d Desktop/AVerMed......
or
sudo alien -d /home/philip/Desktop/AVerMed.....

In other words replace the _ with / character. 

hop it helps :)

---

### Post by taxi16 on 2007-06-12
thanks to all but ,i still canot getit  right .iamsending some  more screenshots  to see if any body can help, if not i will have to go back to ms?[http://ubuntuforums.org/images/uf/attach/png.gifhttp://ubuntuforums.org/attachment.php?attachmentid=35112&stc=1&d=1181631490](http://ubuntuforums.org/images/uf/attach/png.gifhttp://ubuntuforums.org/attachment.php?attachmentid=35112&stc=1&d=1181631490)

---

### Post by peppy.ch on 2007-06-12
I cant find your screen shot's :(

---

### Post by taxi16 on 2007-06-12
hope these are the screen shots?

---

### Post by stchman on 2007-06-12
> **taxi16 said:**
> hope these are the screen shots?

Give us an ls of your /home/philip/Desktop

If it says the file is not there then it is not there.

---

### Post by Calash on 2007-06-12
The V in "AVerMedia" needs to be upper case.  On your screen shot it is lower in your terminal.

So the command should look like this

```

sudo alien -d /home/philip/Desktop/AVerMedia-MTSA-FC4-0.35Beta-1.i386.rpm

```

The best way to make sure the spelling is correct is to use the tab tecnique posted earlier.

So as you are typing you press tab at key points.  ie

sudo alien -d /home/ph

then press tab and it should show you a list of everything that begins with a ph, or if there is only one it will fill in the line for you.  Continue using that same method and you will be sure everything is spelled right.

---

### Post by taxi16 on 2007-06-12
thank u to every 1 for all your help i have managed to create a deb file ,but as u can see it ha s a padlock icon attached?and when i try try 2 install it i get the error shown on the screen shot butthier is only 1 s/ware man tool running:popcorn:

---

