---
title: "Default video editor for Lucid... I'm a little bit sad..."
date: 2009-11-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Keyper7 on 2009-11-22
...that OpenShot earned little more than "the UI sucks" and "it's not intuitive" during the [discussion](http://www.youtube.com/watch?v=olDMAYD7t3k) (video editor part starts at 19:30, openshot part at 26:45). The [blueprint](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-default-apps) still says it will be reviewed and considered, but after seeing the discussion I have little hope. It's not that I don't like PiTiVi, I just feel OpenShot deserved better words.

---

### Post by rylleman on 2009-11-23
Absolutely. It seems like the people at the meeting making the decisions does not know how a good NLE should work. They talk about PiTiVi as an easy option where you can import your footage and get things done without having a lot of extra bling obscuring the workflow.
Well, PiTiVi doesn't even have transitions yet and I'm sure they have a long way to go with a lot of other necessary features as well.
Open shot is on the other hand almost finished as far features go, just some bugs to be ironed out.
I would like to see Kdenlive as the default editor but since it's an Kde-app that will not happen.

---

### Post by Stochastic on 2009-11-24
Well the point was not to include a great NLE on the disks, the point is to give the average user a basic tool for working on their home videos.  I wasn't at the talk, but I would vote for PiTiVi for this purpose myself.  Transitions and titling are coming soon.

OpenShot has yet to make a release, and the current code requires ffmpeg versions that aren't even in Lucid yet.  To quote from their PPA instructions > Our PPA uses a special version of FFmpeg, which does not work with VLC & Totem Last time I checked Totem was pretty central to Ubuntu's multimedia.

My opinion is that PiTiVi isn't perfect, but it's better for the given usecase than anything else at the moment.  OpenShot might become quite useful and stable (never had the courage to ditch my VLC or Totem capabilities to try the UI myself), but I don't think it's ready for Lucid (a Long Term Support release).

---

### Post by Keyper7 on 2009-11-24
> **Stochastic said:**
> Well the point was not to include a great NLE on the disks, the point is to give the average user a basic tool for working on their home videos.  I wasn't at the talk, but I would vote for PiTiVi for this purpose myself.  Transitions and titling are coming soon.

OpenShot has yet to make a release, and the current code requires ffmpeg versions that aren't even in Lucid yet.  To quote from their PPA instructions  Last time I checked Totem was pretty central to Ubuntu's multimedia.

My opinion is that PiTiVi isn't perfect, but it's better for the given usecase than anything else at the moment.  OpenShot might become quite useful and stable (never had the courage to ditch my VLC or Totem capabilities to try the UI myself), but I don't think it's ready for Lucid (a Long Term Support release).

I'm not saying they should've chosen OpenShot, I'm just saying it deserved better words than "OpenShot? The GUI sucks. Anyway, about PiTiVi...". None of the (very reasonable) points you are mentioning here were brought up. The discussion never sounded like "should we include a video editor in Lucid?". From the beggining, it sounded like "should we include PiTiVi in Lucid?".

And by the way, the dependency on newer version of libraries is the way the OpenShot devs originally chose to package it, but it was never necessary (I always used OpenShot with default libraries by getting the tarball instead of the PPA). The new experimental PPA uses default versions even in Karmic: [http://www.openshotvideo.com/2009/11/openshot-ppa-new-experimental-ppa.html](http://www.openshotvideo.com/2009/11/openshot-ppa-new-experimental-ppa.html)

---

### Post by Stochastic on 2009-11-24
Yes, quite often many details of these discussions can't be fit into the allotted time and many of the suggestions have been combed through before arriving.

I do have to laugh a little bit about their suggestion of "Make mixes on the Software Center ("Gimme the graphic designer package")" seeing as there already is the ubuntustudio-graphics package.

---

### Post by cotcot on 2009-11-25
Why not Blender as default ? It is mature and you have 3D animation and a good NLE in 1 program. Easy also for Blender users on Windows platforms to switch to linux. I know some say that Blender is difficult, however the video editor only is very reasonable to learn.

---

### Post by rylleman on 2009-11-25
[Here's]("http://www.omgubuntu.co.uk/2009/11/pitivi-to-become-default-application-in.html") a very interesting article/point of view regarding Pitivi for 10.04.
I agree and think Pitivi is far, far away from being ready for inclusion in any dist. 
People will get dissapointed at the default video editor if that would be Pitivi.

---

### Post by Stochastic on 2009-11-25
> **rylleman said:**
> [Here's]("http://www.omgubuntu.co.uk/2009/11/pitivi-to-become-default-application-in.html") a very interesting article/point of view regarding Pitivi for 10.04.
I agree and think Pitivi is far, far away from being ready for inclusion in any dist. 
People will get dissapointed at the default video editor if that would be Pitivi.

That's not an article, that's a rant.  The poster (and nowhere on his/her site does it reveal their identity) tears into PiTiVi and defends Open Shot - it's hardly balanced.  Furthermore, they've disabled comments on that post for some unadvertised reason.  EDIT: Upon looking carefully I see this post: [http://www.omgubuntu.co.uk/2009/11/pitivi-creator-responds-to-readers.html](http://www.omgubuntu.co.uk/2009/11/pitivi-creator-responds-to-readers.html) where the blog author has granted PiTiVi's creator a (albeit edited with the blog author's opinions) response to the flurry of comments on the original article.

I'll repeat my earlier thoughts that when PiTiVi and OpenShot are compared side-by-side, PiTiVi is clearly much more suitable for inclusion in default Ubuntu.  OpenShot isn't even in the repositories right now so why people are expecting it to become Ubuntu's default is baffling at best.

Cotcot, Blender is an excellent video editor - I agree.  However, for the average user who wants to start a program, click on the 'import' icon, edit their home movie, and save, Blender is just too confusing.  Time and time again, if people ask me what the best video editor is I answer 'Blender' but I certainly wouldn't think it fits the needed 'user-friendly basic editor' role.

---

### Post by jimy_james on 2009-11-28
Although Openshot is very good I believe pitivi will be better.  Openshot is based on MLT 4.6 right now.  This version of MLT doesn't keep the audio and video synched up for flv files, not their fault I know but thats a deal breaker for me, pitivi does not have this problem.  Also Openshot ramps my CPU up to 85% where pitivi runs around 50.  Openshot has alot more in terms of features but many are still buggy but they have yet to have an official release.  Transitions are coming soon in pitivi and once that happens it will be great, thats basically all I need: cut edits and fades.  I see the value and potential in pitivi, for instance the ability to separate video from the audio and the unlimited video and audio tracks.  Once pitivi gets transitions I will probably have to use both programs in conjunction.  Pitivi to set up the movies and then Openshot to add some saturation filters type thing.  Again this is not ideal but pitivi has alot more potencial as far is arrangement of clips I will argue, and is also more stable.

---

