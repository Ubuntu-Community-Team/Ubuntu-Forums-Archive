---
title: "Is there away to make  whatsapp face/video  call in ubuntu 22.04 ??"
date: 2023-12-28
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-12-28
Hi 
Can one do face time/ video call from [https://web.whatsapp.com/](https://web.whatsapp.com/) ???
in ubuntu 22.04 ??
Cheers

---

### Post by hoboy on 2024-01-03
bump

---

### Post by MAFoElffen on 2024-01-03
I would say no. 

First there is no Official Linux WhatsApp Application. 

Next, if you could run it from an emulator, you are not going to be able use a cammera or a WAN card to make the video call.

But, you can run the What'sApp application as a WebAp on Chrome like this: [https://askubuntu.com/questions/684415/install-whatsapp-webapp-on-ubuntu](https://askubuntu.com/questions/684415/install-whatsapp-webapp-on-ubuntu)

---

### Post by mmorse757 on 2024-03-10
I followed the directions for installing Whatsapp as a Chrome app.  I enable several permissions, including audio and video.  Now I can use the audio function by selecting the microphone icon, but there isn't (I don't see one anyway) a camera icon.

---

### Post by TheFu on 2024-03-11
If you absolutely must use whatsapp, you can stop reading this post now.

I've never used facebook/whatsapp with any real information due to privacy concerns.  I understand why it is popular for people who don't care about privacy - at all.  I don't trust facebook. Not at all. I don't even trust them to tell the truth about what they do.

I've used jit.se and nextcloud-talk for video conferencing.  jit.se has a free service anyone can use with just a modern browser. They also have an AppImage electron app (basically a chromimum browser with specific settings to connect to meet.jit.se.  Lots of people like that. I don't see the point. To each their own.
I setup a nextcloud-talk server (really just an addon to my existing nextcloud install) that is fun to use when traveling to talk to people back in the house. Due to my security stance, I require a full VPN for access to anything nextcloud, so it isn't available to the public.
Both Jit.Se and nextcloud-talk have android apps, if that matters.

Jit.Se, assuming you use their servers, isn't secure. It is very democratic and anyone in a meeting is effectively an admin. When you create a room, make certain the room name has a random name to avoid trolls.  The first person to show up to the room has to use outside credentials - I think google is supported.  I don't know. I let others "open" the room.  Also, the video traffic isn't encrypted.

With nextcloud-talk, it will use the https tunnel into the server for each client connection. That's good enough for clients to know their packets aren't modified when connecting to the server.  I don't consider https to be secure enough for any sensitive conversations.  I don't consider any POTS or cellular connections to be secure enough for that either, at least not without a full VPN using IPSec for all traffic.  SSL-based VPNs aren't as secure as people think, but they are usually sufficient for 99% of the world.

I've also used BigBlueButton as a guest only. Seems to work and lets the organizer have more control over the meeting.

[https://www.tomsguide.com/reference/best-encrypted-messaging-apps](https://www.tomsguide.com/reference/best-encrypted-messaging-apps) On my first look, Signal and Wire seem the best options.  Wire doesn't require a phone number to sign up and they did an independent audio in 2017. Take that for what it is - an old audit, but better than nothing.

If you are really nerdy Matrix is looking like the newest, secure, communicate-with-anyone, option.  It is federated and typically setup for others by nerds, like email servers are today.
[https://discussion.fedoraproject.org/t/matrix-chat-four-ways-to-start-video-call/92854#](https://discussion.fedoraproject.org/t/matrix-chat-four-ways-to-start-video-call/92854#)! Looks like Matrix leverages Jitsi stuff for video calls.

---

