---
title: "Will audio and video chat in Empathy be enabled by default in Lucid Lynx?"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bhishan on 2010-04-07
Will audio and video chat for MSN and Gmail in Empathy be enabled by default in Lucid Lynx?

---

### Post by rogerpittman on 2010-04-08
I'm using the Empathy client with Lucid Beta 1, and I don't see any audio/video chat options for either GMail or MSN.

---

### Post by bhishan on 2010-04-08
In Karmic, Ubuntu disabled audio/video support in telepathy-butterfly (the MSN backend) because this new feature got introduced too late and that feature didn't get much testing. What seems to be the reason this time?

---

### Post by shazbut on 2010-04-08
GTalk/jabber should work (windows gtalk clients still have to use gmail web page, I think).
MSN was working in the ppa version, but MS changed the protocol, so now the support has to be rewritten.

---

### Post by philinux on 2010-04-08
Thread moved.

---

### Post by cheapsaket on 2010-04-08
I would like to find out too.

Are there alternatives to Empathy that have working audio & video for MSN?

---

### Post by gnomeuser on 2010-04-08
Microsoft recently obsoleted the old way of doing VoIP and now one can only use the new p2p based protocol. You get 3 guesses as to which protocol hasn't been reverse engineered yet.

Basically there is no way to do this using open source yet.

---

### Post by bhishan on 2010-04-08
> **gnomeuser said:**
> Microsoft recently obsoleted the old way of doing VoIP and now one can only use the new p2p based protocol. You get 3 guesses as to which protocol hasn't been reverse engineered yet.

Basically there is no way to do this using open source yet.

What about Google Talk?

---

### Post by bash on 2010-04-08
Apparently***** the new version of Emesene is still capable of doing MSN/WLM video chat.

***** I have not tried this out myself, so no idea if it actually works.

---

### Post by castrojo on 2010-04-08
> **bhishan said:**
> What about Google Talk?

I've been audio and videoing over gtalk since karmic and it working fine over here.

---

### Post by bhishan on 2010-04-08
> **whiprush said:**
> I've been audio and videoing over gtalk since karmic and it working fine over here.

Can you please explain how?

---

### Post by pjalegria on 2010-04-10
Well, it seems that no one now :lolflag:

---

### Post by manoynmonic on 2010-04-10
voice calls working with empathy over Gtalk, but voice won't work with Yahoo contacts.  Haven't tried msn.

---

### Post by descendent87 on 2010-04-10
Kopete also has voice calls for Gtalk disabled, hopefully they will rebuild and enable it before release

---

### Post by castrojo on 2010-04-10
> **bhishan said:**
> Can you please explain how?

If you're both on gtalk and you're friend has the capability you can just right click on them and video or audio to them. They'll have like a camera or speaker by their icon.

---

### Post by manoynmonic on 2010-04-10
Gtalk works fine for audio - the video wouldn't go for longer than a few seconds before empathy crashes.  The cam works fine with skype video though, so dunno.

---

### Post by bhishan on 2010-04-10
> **whiprush said:**
> If you're both on gtalk and you're friend has the capability you can just right click on them and video or audio to them. They'll have like a camera or speaker by their icon.

It only show microphone but no webcam icon even when my frens have webcam.

---

### Post by pjalegria on 2010-04-11
What about MSN protocol?

---

### Post by amano on 2010-04-11
If I got it right in this thread, MSN switched to a protocol which is not reverse engineered yet. Thus video chatting will not work for MSN until that is done.

---

