---
title: "Rookie Ubuntu User. Having some minor issues."
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2006-07-16
I talked to my buddy last night and he explained to me when I get Linux working I need to install things through the command line. Well, first of all I have no idea where the command line is and on top of that I can't find the right plugins for my audio/video player. Can anybody help? Pretty darn lost...

---

### Post by Jagot on 2006-07-16
The command-line is accessed using a program call Terminal.  You can find this in Applications -> Accessories.  See here:

[http://shots.osdir.com/slideshows/original.php?release=659&slide=74](http://shots.osdir.com/slideshows/original.php?release=659&slide=74)

This link explains all the plugins which are required for media:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This is just a general link which explains about installing stuff which may be of use to you:

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by reacocard on 2006-07-16
you can install via command line. to access it, open Applications -> Accessories -> Terminal. a much easier way to install software is by using synaptic, System -> Administration -> Synaptic Package Manager. for audio and video codecs for totem and rhythmbox, search for gstreamer 0.10.

---

### Post by confused57 on 2006-07-16
You might want to consider Automatix:

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

Also, you may want to read the Sticky "How To Help Yourself" in the "Absolute Beginner" section.

---

### Post by Roasted on 2006-07-16
> **reacocard said:**
> you can install via command line. to access it, open Applications -> Accessories -> Terminal. a much easier way to install software is by using synaptic, System -> Administration -> Synaptic Package Manager. for audio and video codecs for totem and rhythmbox, search for gstreamer 0.10.

What was gstreamer 0.10 supposed to do? I searched for them, found that some were already installed. So I selected the ones that weren't installed yet and installed them. Still, nothing helped. 

Now I'm even more confused as ever because... I'm trying to install Macromedia Flash Player. I'm reading the readme file and following the directions exactly. But when I get to the command line and put in EXACTLY what they tell me to, the terminal tells me they cannot find the file or directory. What's this mean? How can I get around this?

---

### Post by Jagot on 2006-07-16
Did you actually read the Restricted Formats link in my post?  It answers your questions.

---

### Post by Roasted on 2006-07-16
> **Jagot said:**
> Did you actually read the Restricted Formats link in my post?  It answers your questions.

I am right now. I'm a little confused over something. Perhaps I'm just being picky but, with the link you sent me, I'm trying to allow access to these repositories. 

See here:

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=activate-repos.png[/IMG]

The problem I'm having is this. I'm supposed to activate those 3 that share the universe and multiverse attribute. But I don't have any that share the universe and multiverse attribute besides the "backports."

---

### Post by Jagot on 2006-07-16
I'm not at my Ubuntu box so I'm afraid I can't guide you through that.  There is another way however which is easier:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by Roasted on 2006-07-16
Okay well I did that. I assume that is all well and good because I had no errors and followed the directions perfectly. What I'm confused over now is this site... 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It actually says at this one part:

 Ubuntu 6.06 LTS (Dapper Drake)

    *

      Install the following packages to play most proprietary formats using Totem and Rhythmbox, which both come with Ubuntu.
    *

      gstreamer0.10-ffmpeg
    *

      gstreamer0.10-pitfdll
    *

      gstreamer0.10-plugins-bad


It even says install the following packages. But it's not a link, or anything... I don't know how I'm supposed to install something with "nothing."

---

### Post by Jagot on 2006-07-16
Go to Terminal (Applications -> Accessories).  Then type (or just copy and paste these):

```
sudo aptitude update
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
```

If you choose to type them, you need to press 'enter' after each line.

---

### Post by Roasted on 2006-07-16
I appreciate your patience and help, but when I try to play an audio file I still get the same error.

I pasted the 2 lines you said above, put in my password, and hit enter. I got quite a few fast moving lines of what looked to be installation, and it was done. But like I said, same error. :(

---

### Post by Jagot on 2006-07-16
What format are the audio files in?

---

### Post by Roasted on 2006-07-16
MP3 Audio. They were burned onto DVD-R's in data format through Nero in Windows XP last night to back them up. I did that because I took my spare drive, formatted it, and put linux on it. 

I asked my buddy what he thought, and he said he didn't see how burning it in Windows XP would prevent it from working in Linux, since it was just a music file. :confused:

---

### Post by Jagot on 2006-07-16
> **Roasted said:**
> MP3 Audio. They were burned onto DVD-R's in data format through Nero in Windows XP last night to back them up. I did that because I took my spare drive, formatted it, and put linux on it. 

I asked my buddy what he thought, and he said he didn't see how burning it in Windows XP would prevent it from working in Linux, since it was just a music file. :confused:

OK, you have not installed the MP3 codec yet.  Do this:

```
sudp aptitude update
sudo aptitude install gstreamer0.10-plugins-ugly
```

Your buddy is right - it's a fully transferrable file - any operating system will be able to play it with the correct codecs.

---

### Post by Roasted on 2006-07-16
Dude, I love you. It works.

:)

Now I gotta figure out how to use Wine so I can play some GTA San Andreas (assuming it supports it). Any tips or sites where I can learn about that?

edit - I went afk and let my pc idle for about half an hour. Why did it freeze at the screen saver? It didn't freeze last time, but last time I wasn't afk as long.

---

### Post by Jagot on 2006-07-16
For Wine you need to have universe repo enabled.  Then:

```
sudo aptitude update
sudo aptitude install wine
winecfg
```

Not sure it will be able to play GTA though.  A lot of people use Cedega for gaming.  You can check it out here:

[http://www.transgaming.com/](http://www.transgaming.com/)

Not sure about the screensaver issue - might just be a one-off glitch - if it happens again then post about it.

---

### Post by Roasted on 2006-07-16
Hmm, here I am again. When you guys figure out the code to put in the command line, is it something you just know how to do, or is it a certain command you HAVE to get from the readme file of whatever program you download?

I just downloaded the Cedega program, and now I'm just staring at the files and the terminal like... hmm okay, this can't be too hard to figure out, right?

:confused:

---

### Post by Jagot on 2006-07-16
Over time you get to know how to do things.  There should be a readme file with it which should tell you what to do.

You can also have a look at the site which tells you pretty much every way to install software:

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

