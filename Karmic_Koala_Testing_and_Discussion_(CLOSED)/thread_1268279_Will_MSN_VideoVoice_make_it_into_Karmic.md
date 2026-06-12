---
title: "Will MSN Video/Voice make it into Karmic?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cowanh00 on 2009-09-16
As you can read here: [http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy) MSN Video and Voice support has arrived! :guitar:

Will this make it into Karmic? I sure hope so!

---

### Post by Eestlane on 2009-09-17
Great!

---

### Post by Johnsie on 2009-09-17
There is voice and video in the new version of amsn that is in the Karmica repositories. I only tried the video and it was still buggy like the previous version. The new version at least looks a little better, but they still need to put the video into the actual window that you are chatting in rather than a separate video window. Having multiple windows for one conversation doesn't make alot of sense.

---

### Post by gnomeuser on 2009-09-17
The required libraries are nearly all there we are just missing the yet unreleased telepathy-farsight 0.0.13. I have high confidence that this feature will ship with Karmic.

Please note that you may need to install video/audio codec support separately. It wouldn't surprise anyone if these were of the proprietary and patented nature meaning we can't ship them by default. This however should be a simple matter of installing the right gstreamer plugins. *cough* something PackageKit would do for us if we had that *cough*

---

### Post by ELD on 2009-09-17
I agree that the video should be in the same window as the chat (although unsure if you are talking about amsn or emesene here).

+1 vote to having the update included for karmic this is awesome news!

@[gnomeuser]("http://ubuntuforums.org/member.php?u=142879") since empathy is included with gnome, why would such a feature use proprietary tech?

---

### Post by philinux on 2009-09-17
Going the right way for sure.

---

### Post by gnomeuser on 2009-09-17
> **ELD said:**
> 
@[gnomeuser]("http://ubuntuforums.org/member.php?u=142879") since empathy is included with gnome, why would such a feature use proprietary tech?

Because the MSN protocol mandates a certain set of codecs. Now an empathy to empathy chat _might_ have the option to use Theora but if you were to use msn webcam chat the way most of us would, you will be talking to the official client from empathy. This means the two need to find an approved codec with which they can exchange data, meaning the use of the officially approved codecs.

No worries I am sure an open implementation is available as a gstreamer plugin, it should just work once you violate the law (or not depending on the insanity of your local laws).

---

### Post by ELD on 2009-09-17
Ah you make a good point, although i live in the UK which seems i don't fall under these licensing issues (last time i checked anyways).

Would be good if they told us how they did it, so we can see what codecs and such it will use.

---

### Post by Amaranth on 2009-09-17
Empathy could also use the same feature totem does for getting codecs that aren't available. I believe that's actually a gstreamer thing with a hook installed in gstreamer so it shouldn't make empathy depend on packagekit or gnome-app-install.

---

### Post by cowanh00 on 2009-09-21
Sorry to bump this up but any news on if this will hit Karmic? I can't see any reason it won't but it would be nice to have some confirmation. Can I request this somehow to get the ball rolling?

---

### Post by gnomeuser on 2009-09-21
You can follow the progress here:
[https://bugs.launchpad.net/bugs/333675](https://bugs.launchpad.net/bugs/333675)

---

### Post by cowanh00 on 2009-09-21
> **gnomeuser said:**
> You can follow the progress here:
[https://bugs.launchpad.net/bugs/333675](https://bugs.launchpad.net/bugs/333675)

Thanks....

---

### Post by cassidy on 2009-09-21
If you are using Karmic, the telepathy-butterfly package on our PPA should have audio/video support: [https://edge.launchpad.net/~telepathy/+archive/ppa](https://edge.launchpad.net/~telepathy/+archive/ppa)

---

### Post by Claus7 on 2009-09-22
Hello,

this is a long demanding issue (according to my experience) linux users to have a full client, which will support among other things audio and video with their msn counterparts.

I'm using amsn since a lot of time now, and in karmic alpha 6 (and in jaunty) I was able to have video both me and the one I was talking to as well as audio, yet only myself (the one I was talking to, wasn't able to hear me). 

With amsn 0.98, which I think that is in the final stages, and judging from the karmic packages, when karmic will be out, it will have the complete version of amsn, with all these features implemented and running. Just to mention that watching karmic from alpha 5 along with amsn, I have to say that the options which are becoming available to every svn version of amsn are overwhelming (mainly in the audio and video support). It might be that I have not checked the right ones so that the one I'm talking to isn't able to hear me.

I do not understand why is there all the question about it since they have made such a progress all these years. And now in order for someone to install it, someone will be one click away. I have to add, that by judging the offers of every msn clone, amsn is by far the best offering having even more than those features that the original msn offers, and with the advantage of being virus free.

It is a long story among my friends about me receiving a virus from amsn (a file), and as a newby I though back then that it was linux fault that I could not open it. So, transferring it to my windows partition and attempting to open it, suddenly tens of windows appearing in my desktop. I made a strong effort to manage bring my windows partition back into proper life those days.

So, in order to recapitulate. Amsn supports this feature for a long time now, yet it is under heavy development and it is in very good steps for karmic. What I do not know, is now many more features will be implemented in the amsn2, which is a co-effort of amsn and emesene teams now under the roof of amsn logo.

Regards!

We waited for so long and one castle is very nigh in order to fall.

Regards!

---

### Post by rajeev1204 on 2009-09-22
> **gnomeuser said:**
> You can follow the progress here:
[https://bugs.launchpad.net/bugs/333675](https://bugs.launchpad.net/bugs/333675)


Excellent,thanks.

---

### Post by Staz on 2009-09-22
> **Claus7 said:**
> 
So, in order to recapitulate. Amsn supports this feature for a long time now, yet it is under heavy development and it is in very good steps for karmic. What I do not know, is now many more features will be implemented in the amsn2, which is a co-effort of amsn and emesene teams now under the roof of amsn logo.

Note that telepathy (-butterfly) also use the same library that will be used by amsn2 ;)

---

### Post by Staz on 2009-09-22
> **gnomeuser said:**
> The required libraries are nearly all there we are just missing the yet unreleased telepathy-farsight 0.0.13. I have high confidence that this feature will ship with Karmic.

Please note that you may need to install video/audio codec support separately. It wouldn't surprise anyone if these were of the proprietary and patented nature meaning we can't ship them by default. This however should be a simple matter of installing the right gstreamer plugins. *cough* something PackageKit would do for us if we had that *cough*
There is some confusion which is understandable with all the similar names (I made the same error). telepathy-farsight 0.0.11 which is in karmic is sufficient, what is needed is farsight > 0.0.13 and 0.0.15 it's already

---

### Post by rajeev1204 on 2009-10-03
Is this feature in yet? Its been in the PPA for some time now.

---

### Post by Amaranth on 2009-10-03
No, it's considered too unstable for karmic. We'll have it (and have it working well) in lucid though.

---

### Post by nhasian on 2009-10-03
> **Amaranth said:**
> No, it's considered too unstable for karmic. We'll have it (and have it working well) in lucid though.

maybe by then it will have sound effects...

---

