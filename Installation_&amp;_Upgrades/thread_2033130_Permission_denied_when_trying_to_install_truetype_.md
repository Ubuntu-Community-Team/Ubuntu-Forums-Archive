---
title: "Permission denied when trying to install truetype fonts"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by patriot56 on 2012-07-25
Hello forum.
I am attempting to install fonts system wide in Ubuntu 11.10 and am getting a "Permission Denied" error.

What I've done so far....

[LIST]
[*]Downloaded the desired TrueType Font collection into the Downloads directory.
[*]Created a "newfonts" directory in */usr/share/fonts/truetype*
[*]Opened Terminal and entered the command ```
mkdir /usr/share/fonts/truetype/newfonts
```
[/LIST]
Using Nautilus, I navigated to /usr/share/fonts/truetype/newfonts and tried to drag and drop the truetype fonts from the Downloads folder into the /usr/share/fonts/truetype/newfonts directory.  And this is where I get the Permission Denied error.

I have 9 TrueType Font files that I am trying to move into this folder.  I am using Nautilus because I don't know the Terminal command used to perform this task.
I would prefer to use the Terminal.
I understand that I have to use the command ```
fc-cache -f -v
```to make the system aware of the new fonts?

Am I correct in assuming that the appropriate command to move the font files into the "newfonts" directory is ```
mv [sourcedirectory/file] to [destinationdirectory/file]
```?????

I apologize if I have made this more complicated than it needs to be.  It seems I have a way of doing that. :(

Any help is most appreciated.
Thank you in advance.

---

### Post by oldos2er on 2012-07-25
Anytime you want to run file operations outside of your /home/user folder, you need root privileges. In the terminal you use "sudo" to do this, so your command should look something like ```
sudo mv /home/user/Downloads/fonts/* /usr/share/fonts/truetype/newfonts/
``` 

```
gksu nautilus
``` will allow you to drag and drop to /usr/share/fonts/truetype/newfonts/ graphically.

Also you'll need to run the fc-cache command as root too ```
sudo fc-cache -fv
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by patriot56 on 2012-07-25
I am marking this thread [SOLVED] because I found the solution.
And now that I see how simple it is to install fonts in Ubuntu I feel really stupid for even posting this thread in the first place#-o.](*,)  I should have researched it a little further first.:oops:


Here's what I found (for anyone else that is trying to install fonts the hard way).

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

This link explains everything that anyone trying to install fonts in Ubuntu needs to know.

---

### Post by patriot56 on 2012-07-25
> **oldos2er said:**
> Anytime you want to run file operations outside of your /home/user folder, you need root privileges. In the terminal you use "sudo" to do this, so your command should look something like ```
sudo mv /home/user/Downloads/fonts/* /usr/share/fonts/truetype/newfonts/
``````
gksu nautilus
``` will allow you to drag and drop to /usr/share/fonts/truetype/newfonts/ graphically.

Also you'll need to run the fc-cache command as root too ```
sudo fc-cache -fv
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
Thank you [B]oldos2er 
[/B]You must have posted this reply at the same time that I was marking this Thread as [SOLVED] :P
I was feeling a little stupid for even posting this until I read your post.  Now I'm kind'a glad that I did post it.
You have offered some very valuable information regarding how to carry out tasks graphically as root.  Things I didn't know and am excited to learn.
And thank you for the link to RootSudo.  
I assume that the code
gksu nautiluswill allow root access to any of nautilus' functions???

Thanks again mate.  I really appreciate it.

---

### Post by oldos2er on 2012-07-25
> **patriot56 said:**
>  
I assume that the code
gksu nautilus will allow root access to any of nautilus' functions???


Yes, it will, so just tread carefully when using it.  :)

---

### Post by patriot56 on 2012-07-26
> **oldos2er said:**
> Yes, it will, so just tread carefully when using it.  :)

Good advice.  When you consider that the term.....**PEBKAC** was created to describe, *me*. #-o

lol- 

Thanks again oldos2er

---

