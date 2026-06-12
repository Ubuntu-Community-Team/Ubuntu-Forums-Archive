---
title: "I hope there's a way to set default programs for specific file extensions."
date: 2008-06-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-06-12
Like in firefox preferences Applications.

Without the need to find the right file and right click etc.

---

### Post by olskar on 2008-06-12
What is wrong with rightclicking a file and select what program to use with the "Open with" tab?

---

### Post by philinux on 2008-06-12
Many people have moaned about having to do this for every file type. Why not do it all with a nice gui.

System>Prefs>Preferred Apps 

Sound like a good candidate.

---

### Post by olskar on 2008-06-12
Ah ok..well it wouldn't hurt :)

---

### Post by xebian on 2008-06-12
> **philinux said:**
> Like in firefox preferences Applications.

Without the need to find the right file and right click etc.

This has always been around for ages.  In KDE, there is what we call file associations where you set preferred apps for certain file type.  I'm not sure in Gnome, but I'm positively sure there is one if not system wide but in Nautilus somewhere.

In KDE you can do it on the fly when after selecting apps for the first time, you can opt to remember it from that time on as the default app for that file type.

---

### Post by philinux on 2008-06-12
Yes something needs implementing in gnome. The nautilus thing Edit>Prefs media being separate from preferred apps, and the right click thing, causes a lot of frustration from newbies.

Needs consolidating.

---

### Post by MaX on 2008-06-12
Why would you need this?
If your files are not associated with the program you want to use, you should file a bug against that program. If you want to change the default program used then just use the right-click menu. You do it once and you're set.

How many filetypes do you have that doesn't open with the correct program?

---

### Post by philinux on 2008-06-12
Have you tried getting vlc to be the default dvd player instead of totem, it's a pain especially for newbies.

---

### Post by issih on 2008-06-12
I believe that is a bug in the way vlc registers itself with gnome. In general though, I agree it could and should be consolidated into one obvious place. I disagree that things as they are cover every eventuality, open with is ideal for actions that are done occasionally to a file, you should also have the option to define a default action, not just the last used one.

If someone knows how, I'd like to know myself

Hmmn just had a tinker myself, it looks like once you have used more than one app to open a file you can go to any file of that type right click on it and open the properties dialog. You can then set the default for that files type using the open with tab.

Not ideal imho, but at least I know how now :)

---

### Post by philinux on 2008-06-12
> **issih said:**
> I believe that is a bug in the way vlc registers itself with gnome. In general though, I agree it could and should be consolidated into one obvious place. I disagree that things as they are cover every eventuality, open with is ideal for actions that are done occasionally to a file, you should also have the option to define a default action, not just the last used one.

If someone knows how, I'd like to know myself

Yes. agree entirely.

---

### Post by ronacc on 2008-06-12
> **MaX said:**
> Why would you need this?
If your files are not associated with the program you want to use, you should file a bug against that program. If you want to change the default program used then just use the right-click menu. You do it once and you're set.

How many filetypes do you have that doesn't open with the correct program?

almost all of them ,about the ONLY default app I use is nautilus itself and not all the time that .

---

### Post by philinux on 2008-06-18
Newbies converting from windows need an easy to use gui. 

An absolute beginner say being given a link which starts with.

In a terminal do this and edit this config file.... Pretty confusing to a complete linux beginner.

Here's someone who agrees.
[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

---

### Post by Lorenz on 2008-06-18
I'm not even a real noob, but I don't know how to do that and it always annoyed me (I want my movies to open with MPlayer and the music files with Exaile). Would be a great and yet simple feature to have.

---

### Post by MaX on 2008-06-18
> **ronacc said:**
> almost all of them ,about the ONLY default app I use is nautilus itself and not all the time that .

So do it once and save that config file?
Or remove the programs you aren't using and Nautilus will default to whatever is available...

It's such a non issue, if you want a custom system you have to be prepared to do some work.

OR worst case scenario, you are running the wrong distro. Maybe you should use a distro that is more configured to your liking.

---

### Post by philinux on 2008-06-18
> **MaX said:**
> So do it once and save that config file?
Or remove the programs you aren't using and Nautilus will default to whatever is available...

It's such a non issue, if you want a custom system you have to be prepared to do some work.

OR worst case scenario, you are running the wrong distro. Maybe you should use a distro that is more configured to your liking.


Bit harsh.

Did you read this. We are talking about potential converts not die hards like us.
[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

The absolute beginner forum is always full of questions like this.

---

### Post by MaX on 2008-06-18
Yes I read that, I also answered him with the correct way of doing it. It seems like this guy/gal hasn't even tried using the right way of doing it. > What if you want dvd&#8217;s to be opened with vlc instead of totem? What if you want cd&#8217;s to be opened with exaile instead of rythmbox? If you search for files mp3&#8217;s get opened with totem,  &#8230; all these things can&#8217;t be changed with the provided GUI nor with &#8220;gconf-editor". This is a right out lie. This is possible by all means. Just right-click on an Mp3, Choose properties/Open with and select Exaile/Banshee/whatever, if Exaile is not on the list, then file a bug with Exaile, it's it's job to report that it can handle mp3 files. Changing so that DVD's open with VLC is possible with (IIRC) the GUI found in Nautilus preferences, the other stuff you can find in the Preferred Programs application in System/Settings.

What I mean is, if he uses so many different programs than Ubuntu does, he probably should look elsewhere where those programs are provided by default. It's like if I would configure Gnome to open everything in KDE programs. If I wanted that I'd had to work for it. But I probably should just run KDE.

---

### Post by ad_267 on 2008-06-19
I actually like the way this is set up at the moment. Usually I want to change the default application when I'm actually already looking at the file in Nautilus. I don't want to have to go to Preferences > File Types and then shift through a few hundred different file formats.

It's just different to how it is in Windows, that's all. I think it's easier.

---

