---
title: "Microphone does not work in skype"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Asraniel on 2009-03-20
Does anybody else have the problem that the microphone is not working in skype? I heard there are problemes because skype uses oss and now ubuntu has pulseaudio (true?).

The rest is working really well, so i would like to stay on jaunty and not have to go back. (no, my microphone is not on mute, i can hear myself talking over the boxes).

---

### Post by dalonso on 2009-03-20
Have you tried the steps for Skype listed in [http://pulseaudio.org/wiki/PerfectSetup#ThirdPartyApplications](http://pulseaudio.org/wiki/PerfectSetup#ThirdPartyApplications) ???

In previous releases I had to do all of the above steps, but for Jaunty I only needed to:

1) Install libasound2-plugins
2) Finally, open Skype. Set the "Ringing" and "Sound Out" devices to "pulse", then set the "Sound In" to the plughw device of your microphone.

---

