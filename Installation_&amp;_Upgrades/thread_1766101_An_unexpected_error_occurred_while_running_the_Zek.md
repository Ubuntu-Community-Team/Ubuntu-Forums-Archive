---
title: "An unexpected error occurred while running the Zekr on ubuntu 11.04"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by ashah98 on 2011-05-23
I am facing the following error while running the newly installed software ZEKR. I have already installed the latest version of Java.


[B]java.lang.UnsatisfiedLinkError: no pulse-java in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1681)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at org.classpath.icedtea.pulseaudio.SecurityWrapper.loadNativeLibrary(SecurityWrapper.java:27)
	at org.classpath.icedtea.pulseaudio.EventLoop.<clinit>(EventLoop.java:105)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.openImpl(PulseAudioMixer.java:654)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.openLocal(PulseAudioMixer.java:588)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.openLocal(PulseAudioMixer.java:584)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.open(PulseAudioMixer.java:579)
	at org.classpath.icedtea.pulseaudio.PulseAudioDataLine.open(PulseAudioDataLine.java:95)
	at org.classpath.icedtea.pulseaudio.PulseAudioSourceDataLine.open(PulseAudioSourceDataLine.java:75)
	at javazoom.jlgui.basicplayer.BasicPlayer.openLine(Unknown Source)
	at javazoom.jlgui.basicplayer.BasicPlayer.initLine(Unknown Source)
	at javazoom.jlgui.basicplayer.BasicPlayer.startPlayback(Unknown Source)
	at javazoom.jlgui.basicplayer.BasicPlayer.play(Unknown Source)
	at net.sf.zekr.engine.audio.DefaultPlayerController.play(DefaultPlayerController.java:159)
	at net.sf.zekr.ui.AudioPlayerUiController.playerTogglePlayPause(AudioPlayerUiController.java:211)
	at net.sf.zekr.engine.audio.ui.AudioPlayerForm$8.widgetSelected(AudioPlayerForm.java:455)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:234)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1258)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3540)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3161)
	at net.sf.zekr.ui.BaseForm.loopEver(BaseForm.java:34)
	at net.sf.zekr.ZekrMain.startZekr(ZekrMain.java:63)
	at net.sf.zekr.ZekrMain.main(ZekrMain.java:91)
[/B]

Please help to resolve the issue.
Thanks in advance
Regards,
Amir

---

### Post by grundle on 2011-07-21
i'm having the same problem too.
can anyone halp?

---

### Post by drpjkurian on 2011-07-21
This probably means that there is something wrong with your Java
installation, pulse-java is provided by openjdk-6-jre-lib package. Please reinstall it from synaptic package manager

---

### Post by ashawkat89 on 2011-08-09
i'm having trouble using zekr on ubuntu .. it just show me this massage when i tried to open zekr.sh on terminal ...


org.eclipse.swt.SWTError: No more handles [MOZILLA_FIVE_HOME='/usr/lib/firefox'] (java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-mozilla-gtk-3650 in java.library.path
    no swt-mozilla-gtk in java.library.path
    /tmp/swtlib-32/libswt-mozilla-gtk-3650.so: libxpcom.so: cannot open shared object file: No such file or directory
    Can't load library: /tmp/swtlib-32/libswt-mozilla-gtk.so
)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.initMozilla(Unknown Source)
    at org.eclipse.swt.browser.Mozilla.create(Unknown Source)
    at org.eclipse.swt.browser.Browser.<init>(Unknown Source)
    at net.sf.zekr.ui.QuranForm.makeFrame(QuranForm.java:475)
    at net.sf.zekr.ui.QuranForm.init(QuranForm.java:300)
    at net.sf.zekr.ui.QuranForm.<init>(QuranForm.java:278)
    at net.sf.zekr.ZekrMain.startZekr(ZekrMain.java:51)
    at net.sf.zekr.ZekrMain.main(ZekrMain.java:91)
Caused by: java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-mozilla-gtk-3650 in java.library.path
    no swt-mozilla-gtk in java.library.path
    /tmp/swtlib-32/libswt-mozilla-gtk-3650.so: libxpcom.so: cannot open shared object file: No such file or directory
    Can't load library: /tmp/swtlib-32/libswt-mozilla-gtk.so

    at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
    at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
    ... 8 more

---

### Post by the-oggy on 2011-12-20
I had also the same issue in Oneiric.
Solution provided on [https://bugs.launchpad.net/zekr/+bug/783602](https://bugs.launchpad.net/zekr/+bug/783602) didn't work for me
If it also doesn't work for you, try the following:

1) Get the following packages:
        libwebkit-1.0-2_1.2.7-0+squeeze1_amd64 ([here]("http://packages.debian.org/squeeze/libwebkit-1.0-2"))
        libwebkit-1.0-common_1.2.7-3_all ([here]("http://packages.debian.org/sid/libwebkit-1.0-common"))
        xulrunner-1.9.2_1.9.2.17+build3+nobinonly-0ubuntu1_amd64 ([here]("https://launchpad.net/ubuntu/oneiric/+package/xulrunner-1.9.2"))
        and all *deb packages that match your architecture from [here]("https://launchpad.net/%7Ezekr/+archive/ppa/+packages") under label **swt-gtk - 3.6-1~ppa5 **
2) Put all the files in one folder
3) Open terminal, [FONT=Courier New]cd[/FONT] to the folder you put downloaded files in and execute [FONT=Courier New]sudo dpkg -i *

[FONT=Fixedsys]Zekr should be working after the commad is finished without errors[/FONT]
[/FONT]

---

