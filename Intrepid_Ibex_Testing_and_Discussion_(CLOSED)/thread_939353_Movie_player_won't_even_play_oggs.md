---
title: "Movie player won't even play oggs"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrickaupperle on 2008-10-05
I tried to open one of my .oggs to listen to some music and...

---

### Post by Nullack on 2008-10-05
It plays them fine for me. How about your try some debugging yourself or post a sample of the problem file online so I can look at it.

---

### Post by patrickaupperle on 2008-10-05
> **Nullack said:**
> It plays them fine for me. How about your try some debugging yourself or post a sample of the problem file online so I can look at it.

All of my files play fine in vlc. They do not work in exaile or rhythmbox.

Well, it is not helpful but here is terminal output:
```
patrick@patrick-laptop:~/Music/Anti-Flag$ totem 03\ -\ Emigre.ogg 
** Message: Error: Could not get/set settings from/on resource.
gstalsasink.c(528): set_hwparams (): /play/visbin/abin/audiosinkbin/audio-sink/bin6/alsasink1:
Unable to set hw params for playback: Input/output error

```

Here is one of the files. 
[http://www.mediafire.com/?0kk0zxkqjwg](http://www.mediafire.com/?0kk0zxkqjwg)

---

### Post by Hobbes on 2008-10-05
i'll second that.

all of the sudden today when i booted up I can no longer hear any sound. But this includes VLC for me...

vlc error:
```
 unable to commit hardware configuration (Input/output error)

```

totem:
```

Failed to connect stream: Invalid argument
```

banshee:
```
 GStreamer resource error: Failed 
```

system->preferences->sound
```
 audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument 
```

some sort of pulseaudio or gstreamer problem? i'm a little lost here.

thanks for any input

---

### Post by syko21 on 2008-10-05
Make sure the following packages are installed gstreamer0.10-pulseaudio and vlc-plugin-pulse

---

### Post by Hobbes on 2008-10-06
both installed... i have been running intrepid for a little while without any sound problems on this computer, but that just changed today...

when checking if gstreamer-pulseaudio was installed, apt interestingly told me:

"vlc-plugin-pulse is no longer required"

irrelevant, or another clue?

---

### Post by forumache on 2008-10-06
You can try to pulseaudio -k in a terminal, this will kill pulseaudio.
Then start movie player and this time it should pick alsa. Try to play something in movie player. If it works, it means pulseaudio was the culprit. If not, keep digging ;)

---

### Post by Titi on 2008-10-06
i had an error in rhythmbox "couldn't play media" or something like that and movieplayer wouldn't play anything either.
pulseaudio -k solved this problem.
thanks for the tip, forumache

---

### Post by patrickaupperle on 2008-10-06
> **forumache said:**
> You can try to pulseaudio -k in a terminal, this will kill pulseaudio.
Then start movie player and this time it should pick alsa. Try to play something in movie player. If it works, it means pulseaudio was the culprit. If not, keep digging ;)

Thank you. that worked. Is this a permanent fix, or will I have to run pulseaudio -k at every log in?

---

### Post by forumache on 2008-10-06
> **patrickaupperle said:**
> Thank you. that worked. Is this a permanent fix, or will I have to run pulseaudio -k at every log in?

You will have to kill it in every session, but only when you have problems.

On my computer pulseaudio works, but sometimes it has problems and then I kill it.

In the end, it shouldn't create problems and the need to kill it will be eliminated.

If you kill it automatically at every login then you will not know when this is not needed anymore

---

### Post by ronacc on 2008-10-06
I didn't have an ogg to try so I used an mp3 , everything but totem plays it fine including nautilus preview ,totem stalls while starting even without being pointed at a file .output from starting totem from term is .

```
ron@ron-desktop3:~$ totem
** (totem:9981): DEBUG: Init of Python module
** (totem:9981): DEBUG: Registering Python plugin instance: PythonConsolePlugin+TotemPythonPlugin
** (totem:9981): DEBUG: Creating object of type PythonConsolePlugin+TotemPythonPlugin
** (totem:9981): DEBUG: Creating Python plugin instance
** (totem:9981): DEBUG: Init of Python module
** (totem:9981): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:9981): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:9981): DEBUG: Creating Python plugin instance
```

pulseaudio -k does not help this so mabye its something different.

---

### Post by forumache on 2008-10-06
ronacc,

your problem is different. I guess totem is stalling and startup since you activated BBCViewer plugin. It has a known problem, it will try to download a list of videos (or something) and while doing this it blocks everything else... This is a know bug.

Please try without BBCViewer plugin (also I have problems with YouTube plugin, so I disabled both).

---

### Post by Nullack on 2008-10-06
Bizzare that dirac would have rank for decoding mp3 over other decoders. Ill see if I can replicate.

---

### Post by forumache on 2008-10-06
> **Nullack said:**
> Bizzare that dirac would have rank for decoding mp3 over other decoders. Ill see if I can replicate.

Nullack,

it is not related with Dirac and mp3 decoding. It has more to do with BBC content. Please see this bug: 
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959)

It seems that it has been fixed 4 hours ago, so update until you see totem at version 2.24.1-0ubuntu2, although one user complained that there is no BBC content displayed. I'll test it when I'll be at home.

---

### Post by ronacc on 2008-10-06
Thanks forumache , I forgot that I had enabled that for a test awhile ago . With BBCviewer disabled it plays mp3's ok with pulse audio . I wonder why this is only hitting some of us .

---

### Post by Nullack on 2008-10-06
What exactly is bbc content? I thought they are usng dirac

---

### Post by forumache on 2008-10-06
The BBC Content is Radio and Podcasts at the moment. I haven't seen it cause it blocks Totem from starting ;)

See here [https://wiki.ubuntu.com/IntrepidIbex/TechnicalOverview#Totem](https://wiki.ubuntu.com/IntrepidIbex/TechnicalOverview#Totem) BBC plugin

but more of this here: [http://www.linux-archive.org/ubuntu-development/164075-totem-bbc-plugin.html](http://www.linux-archive.org/ubuntu-development/164075-totem-bbc-plugin.html)

I don't know the encoding, is it dirac (which BBC developed), is it mp3, I don't know.

My guess is that it is mp3 encoded to reach a wider audience, and the content is their radio shows.

Now that it seems like the problem with totem and bbc viewer is solved, I hope to see more when I arrive home...

---

### Post by forumache on 2008-10-06
> **ronacc said:**
> Thanks forumache , I forgot that I had enabled that for a test awhile ago . With BBCviewer disabled it plays mp3's ok with pulse audio . I wonder why this is only hitting some of us .

I guess it hits all of Intrepid users, but we are the ones who enabled BBCviewer (not enabled by default). This is what we get when we are playing with the latest and greatest toy ;)

---

### Post by ronacc on 2008-10-06
I wasn.t refering to the bbcviewer issue that has been known for awhile , I just had a senior moment and forgot I had even installed it . I was refering to the not playing sound with pulseaudio which reading the posts dosen't seem to hit all of us .

---

### Post by forumache on 2008-10-06
> **ronacc said:**
> I wasn.t refering to the bbcviewer issue that has been known for awhile , I just had a senior moment and forgot I had even installed it . I was refering to the not playing sound with pulseaudio which reading the posts dosen't seem to hit all of us .

I don't know about you, but once I login I remain logged in for days. As pulseaudio crashes during one session, I am more likely to see it. People who keep their sessions short might not get a chance.

Second, because I use firefox with flash and rhythmbox, all of them interacting more or less with pulseaudio.

Maybe it would be nice to automatically collect from each user a pattern of usage, and link people with similar patterns to see if they hit the same bugs.

---

### Post by ronacc on 2008-10-06
yes my usage pattern on my test box is completley different that box is off most of the time and usually on for only an hour or two when it is on . I use Opera not firefox and rarely visit flash heavy sites and despise rhythmbox so I don't use it at all . Infact I only use totem when someone like the OP requests a test , otherwise it's VLC or Xine .

---

### Post by forumache on 2008-10-06
And here goes my theory about usage patterns ;)

---

### Post by ronacc on 2008-10-06
how does that upset your usage theory ? my pattern IS different and I DON'T see the bug , that should support your theory :)

---

### Post by forumache on 2008-10-06
> **ronacc said:**
> how does that upset your usage theory ? my pattern IS different and I DON'T see the bug , that should support your theory :)

And I (again) remained with the idea that you have problems with pulseaudio, when instead you had problems with BBCviewer plugin.

I am at home now, I applied all the updates, and still BBC plugin doesn't work. It doesn't download anything from BBC, after a delay of minutes, the BBC playlist is empty. I added my experience to 
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959) (which was just declared fixed, although it seems not fixed to me)

---

### Post by ronacc on 2008-10-06
I get the same thing with BBCviewer it waits awhile and then says no content was d/l'd . I hadn't joined in on that bug because I wasn't sure if I should be able to d/l content , even when I try to play some content on the site it tells me I am out of zone or something like that ( I'm east coast US ).

---

### Post by forumache on 2008-10-06
I thought that I'm not allowed too, that's why I asked on the bug if BBC content is restricted to UK. Ivlo answered that it worked for him (before the bug hit) and he is from Russia.

There will be two feeds, one international and one UK only determined by Geo-IP.

P.S. The bug actually is [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/274740](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/274740)
The other one is just for one crash, not interesting for us.

---

### Post by mc4100 on 2008-10-06
The issue that was fixed seemed to be that if content could not be downloaded, the plugin would still be loaded. It's as though the "staging server":
> Totem BBC plugin

Ubuntu 8.10 Beta features a new plugin for the Totem movie player that fetches free digital content from the BBC. To enable it, start Totem (Applications -> Sound & Video -> Movie Player), enable the plugin (Edit -> Plugins -> BBC content viewer) and select "BBC" from the drop-down labelled "Playlist". [i][b]
The feed is fetched from a staging server at the moment so there may be a delay while it is downloaded.[/i][/b] ... is down (can someone check this?) and thus the content feed isn't being retrieved, meaning all one will see in the BBC plugin is an empty window.
To confirm, this **isn't** an issue with location; I'm in the UK and still it does not work.

Edit: There's an update (2.24.1-0ubuntu3) that fixes the empty list issue, but Colin Watson's post on #274740 indicates it's still slow on getting the feed:
> ... You can at least now fetch BBC content again, but network access is still synchronous, so this bug is still open.

---

### Post by forumache on 2008-10-06
It is fixed in totem 2.24.1-0ubuntu3 (the content, not the delay)
It was uploaded, it will appear in the updates list any moment now ;)
We see in history that it was switched to production feed URL.

totem (2.24.1-0ubuntu3) intrepid; urgency=low

  * debian/patches/65_bbc-plugin.patch:
    - Update from Collabora, including:
      + Switch to production feed URL (LP: #274740).
      + Update format mappings, including Ogg, ASF, MP3, Matroska, WMA, WMV,
        Flash video, and Dirac.
      + Take configured connection speed into account when selecting the
        best encoding for an episode.
  * debian/control.in:
    - Depend/build-depend on python-gtk2(-dev) (>= 2.13.0) for BBC plugin.

---

