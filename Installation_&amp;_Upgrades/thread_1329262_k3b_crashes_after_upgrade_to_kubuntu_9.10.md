---
title: "k3b crashes after upgrade to kubuntu 9.10"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by sumpi on 2009-11-17
After the upgrade to kubuntu 9.10, k3b does not seem to be able to start anylonger. I received the following message:
```

 p, li { white-space: pre-wrap; }  Application: K3b (k3b), signal: Segmentation fault
 [Current thread is 1 (Thread 0xb7783920 (LWP 5196))]
 
 Thread 2 (Thread 0xb5762b70 (LWP 5212)):
 [KCrash Handler]
 #6  0x00f46bd0 in K3b::Device::TrackCdText::title() const () from /usr/lib/libk3bdevice.so.6
 #7  0x00f47051 in K3b::Device::CdText::Private::textForPackType(int, int) const () from /usr/lib/libk3bdevice.so.6
 #8  0x00f4b642 in K3b::Device::CdText::setRawPackData(unsigned char const*, int) () from /usr/lib/libk3bdevice.so.6
 #9  0x00f4cba0 in K3b::Device::CdText::setRawPackData(QByteArray const&) () from /usr/lib/libk3bdevice.so.6
 #10 0x00f4cc5b in K3b::Device::CdText::CdText(QByteArray const&) () from /usr/lib/libk3bdevice.so.6
 #11 0x00f249c6 in K3b::Device::Device::readCdText() const () from /usr/lib/libk3bdevice.so.6
 #12 0x003b2ca6 in K3b::Medium::update() () from /usr/lib/libk3b.so.6
 #13 0x003b425a in K3b::MediaCache::PollThread::run() () from /usr/lib/libk3b.so.6
 #14 0x061f2e32 in ?? () from /usr/lib/libQtCore.so.4
 #15 0x00b4e80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
 #16 0x068627ee in clone () from /lib/tls/i686/cmov/libc.so.6
 
 Thread 1 (Thread 0xb7783920 (LWP 5196)):
 #0  0x00168422 in __kernel_vsyscall ()
 #1  0x06854ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
 #2  0x00c1bd80 in ?? () from /usr/lib/libxcb.so.1
 #3  0x00c1c2eb in ?? () from /usr/lib/libxcb.so.1
 #4  0x00c1c687 in xcb_writev () from /usr/lib/libxcb.so.1
 #5  0x008002e9 in _XSend () from /usr/lib/libX11.so.6
 #6  0x007eca8d in ?? () from /usr/lib/libX11.so.6
 #7  0x007ecc5a in XPutImage () from /usr/lib/libX11.so.6
 #8  0x02f62101 in QX11PixmapData::fromImage(QImage const&, QFlags<Qt::ImageConversionFlag>) () from /usr/lib/libQtGui.so.4
 #9  0x02f4e597 in QPixmap::fromImage(QImage const&, QFlags<Qt::ImageConversionFlag>) () from /usr/lib/libQtGui.so.4
 #10 0x02f515d4 in QPixmap::load(QString const&, char const*, QFlags<Qt::ImageConversionFlag>) () from /usr/lib/libQtGui.so.4
 #11 0x02f51d85 in QPixmap::QPixmap(QString const&, char const*, QFlags<Qt::ImageConversionFlag>) () from /usr/lib/libQtGui.so.4
 #12 0x0819ce35 in _start ()

```If triggered from the command line, the following output is shown:
```
~$ k3b
KCrash: Application 'k3b' crashing...
sock_file=/home/sumpi/.kde/socket-querschlaeger/kdeinit4__0
<unknown program name>(5195)/: Communication problem with  "k3b" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

```What should I do? Reinstalling k3b did not help...

Best regards,
Sumpi

---

### Post by artAlexion on 2010-01-01
I aam getting the same errors.  This seems to have happened after installing the Sun VirtualBox (as opposed to the VirtualBox OSE.

Did you report a bug?

My bug reporter apport is crashing as well.

---

### Post by no0ne on 2010-02-09
Same here, crashes with signal 11 when beginning to burn an imagefile.
KDE SC 4.3.5 Kubuntu Karmic i686 running 2.6.31-19-generic.

---

