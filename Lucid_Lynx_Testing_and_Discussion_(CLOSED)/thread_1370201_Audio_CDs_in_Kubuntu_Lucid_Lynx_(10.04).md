---
title: "Audio CDs in Kubuntu Lucid Lynx (10.04)"
date: 2010-01-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brm on 2010-01-02
Trying to listen to audio CDs in the alpha versions of Kubuntu Lucid Lynx (10.04) is proving an exercise in frustration. I am acutely aware of the standard caveats about not using developmental versions of distros for "production purposes." Still, nothing beats "in-the-wild" testing.

My big Core 2 Duo system is currently down. For the time being, I am using an older P4 machine. It has built-in a DVD-ROM (/dev/scd0) and a CD-ROM (/dev/scd1) as well as an external DVD-RW (/dev/scd2). All three drives are, ahem, well used, but I do not suspect hardware failure. I tested with three store-purchased, new, scratch-free CDs. k3b recognized the load of an audio CD into each drive and correctly looked up the freedb metadata for each CD. I'm not having optical drive read problems.

But I have so far been unable to actually play an audio CD in this environment. Amarok 2.2 is supposed to support audio CDs. Whereas the automounter and the system notification both acknowledge the loading of an audio CD into /dev/scd0 (/media/cdrom), Amarok reports that it has zero tracks. Since it reports zero tracks, it plays nothing.

kscd (which has a fancy new interface) behaves even more weirdly. When I put the audio CD into the plainest CD-ROM drive, that is, dev/scd1 (/media/cdrom1, kscd read the track list and pulled down the freedb metadata. However, when I hit play, it complained "no disk." When I hit eject, the draw opened on the external DV-RW drive (/dev/scd2). When I put the CD into /dev/scd0 (the presumed default), the track list came up blank, hitting play produced a "no disk" complaint, hitting eject again opened /dev/scd2. Putting the CD into /dev/scd2 again brought up a blank track list, nothing happened when I hit play, and hitting eject at least opened the drawer containing the CD. The kscd config file is buried deep in the ~/.kde tree, but it appears to have no provision to define the optical drive to be used.

Although not a KDE application, I have had similar frustration with ripperX. Now that grip is no longer included in the repositories, I am looking for a ripper/encoder which allows the user to: (1) define the format for naming folders and files; (2) calls musicbrainz.org for tag data; and (3), allows the user to set precise encoding parameters. Extensive Googling suggested that ripperX does not allow quite the precise level of control that grip did, but it comes closer than anything else. However, regardless of which drive I tried putting the audio CDs in, ripperX consistently complained that it could not find an audio CD. Like kscd, the config file, ~/.ripperXrc appears to lack provision to define the optical drive to be used.

All this is enough to drive a user back to ExactAudioCopy --- a one man effort which stands out as evidence that some Windows applications reflect the Unix philosophy of doing one small task and doing it very well. No, I am not about to abandon Linux after ten years of enthusiastic use, but this has been a *_very frustrating_* day (see also my message about printing from KDE applications).

Before I file bugs at Launchpad (the Kubuntu bug tracker) and on the KDE Bugzilla, I would be interested to know if others have noted a similar problem.

I will be posting this message on ubuntuforums.org, kubuntuforums.net and to the kde-linux mailing list.

---

### Post by phillw on 2010-01-02
I do recall seeing a bug for CD's only playing the 1st track.. Or maybe it was the bug-fix going into the build. Someone suggested I subscribe to the updates mailing list for 10.04 - Which is actually really kewl, I sorta understand 50% of what they're on about - But it does allow me to information overload several times a day as they update the daily image.

Like I say, I do recall one flying past for problems with CD's.  Leave it be for 48 hours, it should hit the repositries.

I've had a quick look thru' my archived mail, but cannot find it.

This thread will allow you to keep a track of where various packages are up to --> [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

Don't be fooled by the title - there is an immense amount of information in that thread.

Errm, yeah, you'll see my embarrassing bit about trying to learn how to use it - So, don't feel like a noobie :lolflag:

It does take a while to get your head around what the devs are up to & they speak in a language that can be loosely translated as english :)

So, don't post asking what xyz is doing - go and find out !! - It's great fun :)

Regards,

Phill

---

