---
title: "problem with edgy"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by vatzcar on 2007-01-04
Hi,
recently i've moved from ubuntu 6.06 to ubuntu 6.10. previously i was using ubuntu 6.06 without any problem with xine, wine, and few other stuff installed. during the installation process i didn't have any upgrade option, so i had to re-install the whole os. now i'm facing following problems:

1. whenever i'm using the command(except first time after each boot) 'sudo nautilus', it's not asking me for password.
2. at the time of executing the above command an error is showing, and my mounted partitions are not coming within nautilus.
```
(nautilus:22819): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
```
3. if i'm browsing my vfat partition the following messing is showing(only for few folders)
```
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)208, height=(int)176, codec_data=(buffer)00000000
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)22050, channels=(int)1, codec_data=(buffer)040080bb000008000000000000000000000000000000
totem-video-thumbnailer couln't open file 'file:///media/sdb7/mov03287.avi'
Reason: You do not have a decoder installed to handle this file. You might need to install the necessary plugins..
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)208, height=(int)176, codec_data=(buffer)00000000
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)22050, channels=(int)1, codec_data=(buffer)040080bb000008000000000000000000000000000000
totem-video-thumbnailer couln't open file 'file:///media/sdb7/mov03288.avi'
Reason: You do not have a decoder installed to handle this file. You might need to install the necessary plugins..
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)208, height=(int)176, codec_data=(buffer)00000000
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)22050, channels=(int)1, codec_data=(buffer)040080bb000008000000000000000000000000000000
totem-video-thumbnailer couln't open file 'file:///media/sdb7/mov03290.avi'
Reason: You do not have a decoder installed to handle this file. You might need to install the necessary plugins..
```
it's all 'bout totem and codec, but there's nothing to do with that as i'm just browsing one folder in my vfat partition.
4. when i'm going to install xine. running './configure' and error is coming that xine configuration failed due to non existence of libpng. where i'm installed with libpng (even with libpng-dev)
5. whenever i'm trying to run wine, a folder access error is coming.
6. my ATI control panel is not also working. it can't find out 'fireglcontrolpanel'.

i'm totally updated with all my installed stuffs. i've tried to re-install edgy over and over. my partition is like this

root - on extended partition residing with another vfat partition.
swap - on same extended partition.
home - on a primary partition.
my disk have partition like this
{primary partition - NTFS}
{primary partition - [extended partition - vfat, ext3(root), swap]}
{primary partition - ext3(home)}

my previous 6.06 installation was perfectly working. please help me to solve this problem. thank you.

---

### Post by meng on 2007-01-04
1. If you give the password for sudo once, it stays in effect for 10 minutes or so if you execute subsequent sudo commands.
2. That message always comes up. Don't worry about it. You're better off using gksu nautilus than sudo nautilus. Even so you'll still get a message.
3. I think this has to do with GNOME trying to generate thumbnails/previews of media files, even if the appropriate codecs are not installed. Either install the codecs or turn off the previews (Edit > Preferences > Previews IIRC)
4. Install xine from repositories rather than from source. THat should solve it.
5. Not sure
6. Not sure, look at the cchtml wiki on installing ATI in edgy.
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by vatzcar on 2007-01-04
thanks meng for your quick reply. i'll try to install xine from repos. but my main problem is wine. i've shifted to edgy just because of wine. as two of my winapps were not performing good at all in 6.06. :( 

thanks for your help :)

---

### Post by vatzcar on 2007-01-05
okay another thing, is someone can just explain me please. why all these problem i'm facing while there wasn't a single problem in my last ubuntu 6.06? sencondly, what do i do if any thing i need to compile and that requires libpng?
do you think it would be better if i revert to 6.06 and try to upgrade to 6.10, after installing all the required software?
any help or suggestion would be very nice. thanks

---

