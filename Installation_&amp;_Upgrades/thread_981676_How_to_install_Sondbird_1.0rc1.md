---
title: "How to install Sondbird 1.0rc1"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by chrismja on 2008-11-13
I am pretty new to Ubuntu and have learned/am learning alot, but here is my question: I currently have Songbird 0.7.0 installed and I have downloaded the new Songbird 1.0 rc1 and would like to install it. It is in a compressed .tar.gz format. I know how to extract the files, but I can't figure out how to install it. Can anyone give me any help? Thanks

---

### Post by inobe on 2008-11-14
thats a tough one !

is that a source tar ball ?

if yes then open terminal and cd the directory' then do

```
./configure
       make
       make install
```

you may encounter dependency issues, read the documentation to be aware of what's ahead.

---

### Post by Bops on 2008-11-14
How did you install the 0.7.0??

I have downloaded the tar.gz. file, but i can't install it. I've googled and googled and followed numerous code instructions, but I seem to have some problems with directories or acces to these??

Any help appreiciated.

Thanks 

Bo

---

### Post by mc4man on 2008-11-14
> How did you install the 0.7.0??

For 0.7 you could just install from the .deb here (hardy 32 bit, links for 64 bit, intrepid on bottom of page
[http://www.getdeb.net/search.php?search_distro_id=9&keywords=songbird](http://www.getdeb.net/search.php?search_distro_id=9&keywords=songbird)

Building latest version isn't too involved, ck. songbird home page for info if needed

---

### Post by chrismja on 2008-11-14
> **inobe said:**
> thats a tough one !

is that a source tar ball ?

if yes then open terminal and cd the directory' then do

```
./configure
       make
       make install
```

you may encounter dependency issues, read the documentation to be aware of what's ahead.

I've tried installing using these commands, but it doesn't work. I installed 0.7.0 using a .deb file found at getdeb.com, but they don't have the 1.0rc1 on there yet. I've also searched the Songbird website and alot of people are talking about it, so obviously they have been able to install it, but no mention of how to. If I find out, I'll post the info here....

---

### Post by chrismja on 2008-11-14
Follow this link. Very good instructions on how to install Songbird. Just replace the filename with the filename of the version you are installing.

[http://luisgmarine.blogspot.com/2008/03/how-to-install-songbird-on-ubuntu.html]("http://luisgmarine.blogspot.com/2008/03/how-to-install-songbird-on-ubuntu.html")

---

### Post by joerdie on 2008-11-28
> **chrismja said:**
> Follow this link. Very good instructions on how to install Songbird. Just replace the filename with the filename of the version you are installing.

[http://luisgmarine.blogspot.com/2008/03/how-to-install-songbird-on-ubuntu.html]("http://luisgmarine.blogspot.com/2008/03/how-to-install-songbird-on-ubuntu.html")

Everyone keeps sending me to this guys link. As far as I'm concerned hes speaking in tongues. I literally couldn't understand less what he is talking about. 

I am extremely new to Linux and need step by step instructions. Are their any other tuts? Thanks.

---

### Post by JeppeM on 2008-12-02
All the things written in *italics* in that guide needs to be entered into the Terminal. You can find this in Applications --> Accessories

---

### Post by josaphat on 2008-12-09
> **joerdie said:**
> Everyone keeps sending me to this guys link. As far as I'm concerned hes speaking in tongues. I literally couldn't understand less what he is talking about. 

I am extremely new to Linux and need step by step instructions. Are their any other tuts? Thanks.

Those *are* step by step instructions. Here's some help understanding each step:
1: Get the files you need to install.
2: The files come packaged in a format referred to as ".tar"; so to extract them from this package deal that they're in (like a box), you need to run a program to do it. That's what that command is for. Just type that into a terminal [ Applications -> Accessories -> Terminal ]
3: By default, the file system doesn't give users write permissions. Only root can change those files. (Root is the "super-user" of the computer. You don't make an account for root, its already there, and you should have made a root password when you installed Ubuntu). You can get permission to change those files as a regular user by typing in that command, but instead of "username:username" type in your ubuntu login name.
4: You're going to add all the shortcuts and goodies to your menus so you can access Songbird easily. This command opens up a text editor (like notepad).
5: Copy and paste that text, but you need to replace the fifth line with where you saved the songbird icon. Snoop around google for an icon you want to use and save it in the folder /opt/Songbird/. Just modify the line to the correct filename.

For the rest just type everything in and follow exactly as it says. I suggest researching the web for things like "shebang", "bash commands". Just click links for a while and learn what you can.

I know that's kind of long. Hope that helps.

---

