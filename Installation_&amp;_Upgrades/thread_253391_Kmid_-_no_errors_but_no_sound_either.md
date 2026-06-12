---
title: "Kmid - no errors but no sound either"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-09-08
Is Kmid program supposed to be able to play midi files under either Ubuntu (gnome) Dapper Drake or Ubuntu Edgy Eft ?

I have tried several times to get it to work under Dapper and last night I also tried it on a test install of Edgy.

When I open Kmid and point to a midi file, the program appears to be functioning, bar goes across, blinking lights, displays text of midi file, etc. but NO sound.

And yes I do have to sound turned up and I can play wav files and other system sounds just fine.

Thanks.

---

### Post by jonnywilkinson on 2007-10-22
You need to install the packages kcontrol and  kdemultimedia. You can then set up your sound and use mixer to switch on the various psorts

---

### Post by sgtbob on 2007-10-27
I have a similar problem trying to play .mid files.  

I DL the kcontrol and kdemultimedia items as suggested.  The only place I can access items is to select the 'desktop' and drag the files to it; however, kmid still does not have sound.  As noted, lights go on, the title appears, and if I select another .mid file, I am told that a 'song is already playing' - but no sound.  As a matter of fact, I can not get anything to play on kmid - any ideas?

I have audacious and music will play on it, but not .mid files.  I'm presuming that kmid is the only way to play these - right?

Bob

---

### Post by gobuntu on 2007-11-07
> **sgtbob said:**
> I have a similar problem trying to play .mid files.  

I DL the kcontrol and kdemultimedia items as suggested.  The only place I can access items is to select the 'desktop' and drag the files to it; however, kmid still does not have sound.  As noted, lights go on, the title appears, and if I select another .mid file, I am told that a 'song is already playing' - but no sound.  As a matter of fact, I can not get anything to play on kmid - any ideas?

I have audacious and music will play on it, but not .mid files.  I'm presuming that kmid is the only way to play these - right?

Bob

Hi Bob,

KMid is a Karaoke/MIDI 'player' which needs a MIDI synthesizer (the engine: can be: hardware or software, that produces instrument voices, same as in Windows, based on data input).

When KMid is not making sound, but shows words and movement of a kar file, or MIDI file, if one installs Timidity via Synaptics, then instruments will be played (sound output).

Timidity IS a good software synthesizer. 

Once Timidity is installed, in Kmid, go to Settings/MIDI Setup and select Timidity.

I think that although there's more MIDI around Windows currently, the architecture of ALSA and MIDI has more potential than Windows, overall.

You might need to add medibuntu repository to install Timidity.

Once you have Timidity installed, you have the like of the Windows MIDI engine, meaning that sites that play MIDI will make sound, or whichever other MIDI input calls for sound.

Kmidi would be technically an 'interface', rather than a "player", but then again, it's terminology, because a soft-synth does not 'play' by itself, either, it neees MIDI data in.

You might look at it this way, if it helps: nothing 'plays' by itself, although they be called 'players'.

Kmid with Timidity (Software Synthesizer) works very well for me fine in Gutsy.

Hope you resolve too.

---

### Post by angryforumreader on 2008-04-06
Thanks a lot for that last reply. I thought it was my midi that was not work. Turned out Kmid is the one with the problem. Thanks again!

---

