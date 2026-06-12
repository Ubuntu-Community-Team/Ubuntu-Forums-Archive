---
title: "Can an ISO be fixed ?"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by oygle on 2010-06-25
Have downloaded the AMD64 and the i386 'esktop' ISO images. Downloaded the MD5SUMS file, and then ran md5sum against the ISO's. The i386 desktop MD5 doesn't agree with the value in the file MD5SUMS

I can open the ISO image with archive manager. Have just spend about 2 hours downloading it, and have limited bandwidth. I don't really want to download it again.

Is there a way to "fix" the ISO ?

Oygle

---

### Post by confused57 on 2010-06-25
The only way I can think of that might work is to download the small torrent file, then when asked where to save the iso, select the location of your downloaded i386 desktop iso.
  
If it's just a matter of a few parts missing, it may  download just those parts.

---

### Post by oygle on 2010-06-26
> **confused57 said:**
> The only way I can think of that might work is to download the small torrent file, then when asked where to save the iso, select the location of your downloaded i386 desktop iso.
  
If it's just a matter of a few parts missing, it may  download just those parts.

I have never used bit torrent before. Actually downloaded the whole ISO again with bit torrent. After it finsihed downloading, it started to upload ??

Anyway, I cancelled after the uploads commenced. The resultant ISO didn't return a checksum (md5) value, it just hung there, so I parsed the "-warn" option, and it gave a heap of "improperly formatted checksum lines".

So, I won't be trying bit torrent again, I guess the whole file sharing thing I don't agree with anyway, I'd rather download from a reliable source.

The first time I downloaded the (i386/desktop) ISO, I used wget. It has worked fine for me previously though, and the AMD64 ISO was okay (md5 sum).

Have seen lots of other posts about people having trouble with the ISO's, or they download okay, but then can't boot.

Is 10.04 a reliable release ?

Oygle

---

### Post by dino99 on 2010-06-26
make your choice

[http://ftp.oleane.net/ubuntu-cd/10.04](http://ftp.oleane.net/ubuntu-cd/10.04)

---

### Post by oygle on 2010-06-26
Thanks everyone for your help. Have _finally_ downloaded a i386 ISO that agrees with the file MD5SUMS. It took 3 full downloads (2.1Gb - half my monthly quota  :mad: ). Here is the summary

1. Using wget on [http://releases.ubuntu.com/releases/lucid/ubuntu-10.04-desktop-amd64.iso](http://releases.ubuntu.com/releases/lucid/ubuntu-10.04-desktop-amd64.iso)  -  **OKAY**, first time

2. Using wget on [http://releases.ubuntu.com/releases/lucid/ubuntu-10.04-desktop-i386.iso](http://releases.ubuntu.com/releases/lucid/ubuntu-10.04-desktop-i386.iso)  -  MD5 didn't agree

3. Used bit torrent by downloading [http://releases.ubuntu.com/releases/lucid/ubuntu-10.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/releases/lucid/ubuntu-10.04-desktop-i386.iso.torrent) first, and then ran Transmission BitTorrent client. It downloaded okay, but the MD5 sum didn't agree

4. Using wget on [http://ubuntu-releases.optus.net/lucid/ubuntu-10.04-alternate-i386.iso](http://ubuntu-releases.optus.net/lucid/ubuntu-10.04-alternate-i386.iso)  -  md5 is now **OKAY**  :popcorn:

---

### Post by tgm4883 on 2010-06-26
> **oygle said:**
> I have never used bit torrent before. Actually downloaded the whole ISO again with bit torrent. After it finsihed downloading, it started to upload ??

Anyway, I cancelled after the uploads commenced. The resultant ISO didn't return a checksum (md5) value, it just hung there, so I parsed the "-warn" option, and it gave a heap of "improperly formatted checksum lines".

So, I won't be trying bit torrent again, I guess the whole file sharing thing I don't agree with anyway, I'd rather download from a reliable source.

The first time I downloaded the (i386/desktop) ISO, I used wget. It has worked fine for me previously though, and the AMD64 ISO was okay (md5 sum).

Have seen lots of other posts about people having trouble with the ISO's, or they download okay, but then can't boot.

Is 10.04 a reliable release ?

Oygle

To answer your post.

Yes, once it is down downloading it just uploads. News flash, it uploads while you are downloading.

It didn't hang there, likely it was computing the checksum. It take a minute or so to do that. Not sure why you got the "improperly formatted checksum lines" errors, where did you download the md5 from?

I'm not sure why you think bittorrent isn't a reliable source for the files. Canonical provides the torrent files and you can verify the md5sum against the once from Canonical if you really want. Although thats not really needed because it checks the parts that it is downloading. I would go as far as saying that bittorrent is **more** reliable than wget.

10.04 is a reliable release. People have issues for different reasons.

---

### Post by oygle on 2010-06-26
> **tgm4883 said:**
> Not sure why you got the "improperly formatted checksum lines" errors, where did you download the md5 from?

From [http://ubuntu-releases.optus.net/lucid/MD5SUMS](http://ubuntu-releases.optus.net/lucid/MD5SUMS)

> **tgm4883 said:**
> 
I'm not sure why you think bittorrent isn't a reliable source for the files. Canonical provides the torrent files and you can verify the md5sum against the once from Canonical if you really want. Although thats not really needed because it checks the parts that it is downloading. I would go as far as saying that bittorrent is **more** reliable than wget.

Hmm, okay. I guess I assumed that bit torrent was P2P, and that the file/s were being downloaded from various 'computers', just like normal P2P. But it appears that if Canonical provides the torrent files, then they are from reliable source/s.

> **tgm4883 said:**
> 
10.04 is a reliable release.

Okay, thanks for your help. Possibly I will use a more local repository (like Optus) the next time. I don't know why the official Ubuntu i386 desktop ISO didn't agree on the MD5sum. I have used wget a lot of times, but must say I liked the interface on the bit torrent side of things.

Thanks,

Oygle

---

### Post by tgm4883 on 2010-06-26
Bittorrent is P2P, but you would need to understand bittorrent/p2p/md5hashes more to know why that is reliable

---

### Post by cpmman on 2010-06-26
Try _***[zsync]("http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/")***_ - it only downloads differences.

---

### Post by tgm4883 on 2010-06-26
> **cpmman said:**
> Try _***[zsync]("http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/")***_ - it only downloads differences.

Oh yea, I totally forgot about zsync. Zsync FTW!

---

### Post by oygle on 2010-06-27
> **tgm4883 said:**
> Bittorrent is P2P, but you would need to understand bittorrent/p2p/md5hashes more to know why that is reliable

I'm quite happy to use BitTorrent, as long as ..

1. Any/all downloads are only from Ubuntu repositories. That is, the source must be officailly recognised by Ubuntu. I don't want anything dodgy downloaded to the computer.

2. Nothing is uploaded at all (except ENQ/ACK type packets).

> **cpmman said:**
> Try _***[zsync]("http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/")***_ - it only downloads differences.

Okay, thanks. Sounds like zsync is better than bittorrent.

Thanks,

Oygle

---

### Post by tgm4883 on 2010-06-27
> **oygle said:**
> I'm quite happy to use BitTorrent, as long as ..

1. Any/all downloads are only from Ubuntu repositories. That is, the source must be officailly recognised by Ubuntu. I don't want anything dodgy downloaded to the computer.

2. Nothing is uploaded at all (except ENQ/ACK type packets).


1) If you get the .torrent file from Ubuntu.com, then yes it is recognized by Ubuntu. You will be downloading the ISO through bittorrent from other users (non-canonical users). The fact that you think that it is dodgy suggests that A) You completely misunderstand how bittorrent works and B) Have let the media decide for you what bittorrent is.

2) I'm not sure why you are so against the uploading part, unless you have bandwidth limits on uploading. You could configure your upload speed to be restricted or download a bittorrent client that allows you to turn off uploading.

---

### Post by oygle on 2010-06-27
From [BitTorrent optimization and troubleshooting guide - Security](http://ubuntuforums.org/showthread.php?t=1259923) ..

> 
As already explained, the BitTorrent protocol is much more secure than other file sharing networks, because you do not grant anyone the rights to browse your folders. But a torrent client is essentially a server and thus will be listening to a port for incoming connections. **This means anyone can connect to you without your request**, as long as they are using a compatible BitTorrent client and sharing the same file through the same tracker. This is obviously wanted, to maximize the number of potential connections with other peers, since the download speed depends on being connected to several of them, as already explained in the Download Speed section. Nevertheless, _some people might try to use this opened pathway to your computer to gain unauthorized access to other resources on your machine_.

In a normal situation, the BitTorrent client will not allow any access to your computer other than transferring pieces of the file specified in the torrent metadata, between both connected peers. **Nevertheless, security holes exists in any kind of software**. So, _if your torrent client has a security vulnerability, it could be used to gain access to other resources on your machine_. Fortunately, there are lot's of people in the open source community that tries to find those flaws in applications and alert the community about possible risks. To minimize the risks you should always keep your system and torrent client updated with the latest patches.

Having an updated system is essential for any Internet activity, but does not guarantee your immunity, since an attacker could be exploiting a security flaw that hasn't been discovered or fixed by the application developers, which are known as "zero-day exploits". To protect your machine against "zero-day attacks", you can use Apparmor to limit what resources and permissions are granted to your BitTorrent client, thus limiting what an attacker could do if he gains full control of your client. More about Apparmor at [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)


Obviously, using a tool such as 'wget' is much safer than BitTorrent, for the simple reason than wget downloads from the one (authorised) source, whereas BitTorrent downloads from multiple (unauthorised) sources. By using the term 'unauthorised', this is indicative of 'sources' I am not aware of, sources that are from 'non-canonical users'. **I do give my permission to share files with such parties.**

We use broadband wireless for internet conection, and uploads are counted towards the quote, which is not huge per month. I did notice that the bandwidth meter, whilst using BitTorrent was **much** higher than it was for the same file, using wget. This would indicate, that even though I did not give permission for any files to be uploaded via BitTorrent, they were uploaded anyway.

I want full control of files I download, and files I upload, and do not want to leave it up to some app to decide. Nor do i want to leave an open door anywhere.

File sharing, ........ no thanks.  ;-)

Oygle

---

