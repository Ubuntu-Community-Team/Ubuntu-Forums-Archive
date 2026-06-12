---
title: "lost desktop"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by boyrobson on 2013-03-07
So, I was annoyed with my ubuntu oneiric only giving me the partial upgrade option so I went ahead and edited my sources changing every instance of "oneiric" to "raring" hoping I would get the latest version of ubuntu (not doing any research as i've been feeling quite lazy today). The upgrade went through successfully.

Now here is my problem. All I have is a blue desktop upon logging in. no menu, no files on the desktop. NOTHING. The only thing that will work for me is my shutdown button and ctrl-alt-delete.

Is there any way I can get back to a more stable version of ubuntu?

thanks.

Jake.

---

### Post by boyrobson on 2013-03-07
[COLOR=#000000]So, I was annoyed with my ubuntu oneiric only giving me the partial upgrade option so I went ahead and edited my sources changing every instance of "oneiric" to "raring" hoping I would get the latest version of ubuntu (not doing any research as i've been feeling quite lazy today). The upgrade went through successfully.[/COLOR]

[COLOR=#000000]Now here is my problem. All I have is a blue desktop upon logging in. no menu, no files on the desktop. NOTHING. The only thing that will work for me is my shutdown button and ctrl-alt-delete.[/COLOR]

[COLOR=#000000]Is there any way I can get back to a more stable version of ubuntu?[/COLOR]

[COLOR=#000000]thanks.[/COLOR]

[COLOR=#000000]Jake.[/COLOR]

---

### Post by stinkeye on 2013-03-07
I'm feeling quite lazy today too.
Use a live cd/usb to backup what you want in your home folder and reinstall.

---

### Post by ventrical on 2013-03-07
No terminal either?? 

ctrl+alt+F1

---

### Post by dino99 on 2013-03-07
you cant do a so huge jump; there is a too big difference .
you are now ready to install a fresh raring  ):P

---

### Post by boyrobson on 2013-03-07
> **ventrical said:**
> No terminal either?? 

ctrl+alt+F1

nope i'm afraid not.

don't suppose somebody will be able to link me to a video to make a bootable usb drive using a mac?

---

### Post by boyrobson on 2013-03-07
I don't suppose you will be able to help and or link me to a video which could show me how to make a bootable usb drive on a mac?

thanks.

---

### Post by craig10x on 2013-03-07
A fresh install of 13.04 (using a daily build) would be your best bet...13.04 has been very reliable considering it is still going through testing and hasn't been final released...don't just by the huge jump you made with the upgrade...it has been remarkably trouble free...only had one minor breakage (vlc media player sound) which was fixed within 3 days (came through in the updates and i just had to reset the vlc media player setting for pulse audio again)...otherwise, updates have been very smooth...

---

### Post by EgoGratis on 2013-03-07
Try to get in command line from Grub rescue mode (latest kernel rescue mode) and if you have working internet connection (cable connected) try to:

1.) Remove and then install ubuntu-desktop package.
2.) Remove proprietary driver for AMD or Nvidia graphic card and start Ubuntu again.

Probably it is driver issue and you have to somehow remove the blob installed from Oneiric something like sudo apt-get remove fglrx* or sudo apt-get remove nvidia-* but because this method of upgrading Ubuntu (much too many versions in between) is not officially supported you might be better off doing a clean install but i would not use Ubuntu 13.04 for daily usage because it can brake and then you don't have working OS on your PC anymore.

---

### Post by stinkeye on 2013-03-07
Gee you are lazy. :P
Search youtube. "[**_[COLOR="#B22222"]how to create a bootable ubuntu usb stick on os x[/COLOR]_**]("http://www.youtube.com/results?search_query=how+to+create+a+bootable+ubuntu+usb+stick+on+os+x+&oq=create+a+bootable+ubuntu+USB+stick+on+OS+X&gs_l=youtube.1.0.0i5.3718.3718.0.7284.1.1.0.0.0.0.293.293.2-1.1.0...0.0...1ac.2.Juf3DGDVeqI")"

---

### Post by EgoGratis on 2013-03-07
> **boyrobson said:**
> nope i'm afraid not.

don't suppose somebody will be able to link me to a video to make a bootable usb drive using a mac?

Here you go:

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

UNetbootin for GUI method or dd in the command line but be careful if u will use dd to not overwrite accidentally something else and not your USB drive.

---

### Post by sandyd on 2013-03-07
threads merged

---

### Post by boyrobson on 2013-03-08
I want to do a fresh instal however i only have a mac to do this on. All the youtube videos seem rather vague and ambiguous. It does explain on the ubuntu website however it always loses me. If anybody could break that down for me to make it simpler? Would be extremely grateful as I am stuck with no laptop :( [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) here's the link to Ubuntu's official guide.

---

### Post by boyrobson on 2013-03-08
right. New problem. I have a live usb all up and ready. However i want to rescue my files from my old file system before i do a fresh installation of ubuntu. How can i do this as it says i do not have root permissions. I have tried 'gksu nautilus' and this has not been successful. Can anybody shed some light on this situation? Thanks.

---

### Post by black veils on 2013-03-08
is your home encrypted? if yes, do this:

```
sudo ecryptfs-recover-private
```

The command will offer to recover an encrypted directory if it locates one.

Assuming the command found a wrapped passphrase file on your system, it  will prompt you for your login passphrase. If it doesn’t find this file,  you’ll need the mount passphrase – hopefully you have a copy of this. If you don’t, you can’t recover your files.

The passphrase will mount the encrypted directory in your /tmp directory. use ```
gksudo nautilus
``` to view it.

source/guide [http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

