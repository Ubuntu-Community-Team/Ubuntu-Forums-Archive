---
title: "New install 12.04 x64 - 4x3TB RAID5 Volume size incorrect"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by macsli1 on 2012-07-06
I'm setting up a RAID5 on a new file server / media center and I'm running into an issue with UBUNTU setup.

I configured the BIOS and setup Intel RST with a 8.1TB Volume (3 Data - 1 Parity - 4X2.7TB)
But, when I run the install cd, it comes up as a 2.4TB volume???
(Tried both the standard and alternate install iso)
:confused:

I've spent the last few hours going through blogs, manuals, and forums to figure out how to fix this but I can't seem to find something that tackles +2TB drives/48-bit LBA, RAID5, and all this while installing.
](*,)

Anyone have any ideas on what I should do?
Any helpful links I may have missed?

Here's a brief of my setup:
[ASRock Z77 Pro3 Mobo]("http://www.asrock.com/mb/Intel/Z77%20Pro3/")
4x3TB Segate Barracudas in RAID 5 (9TB)
Intel RST version 11.0.0.1339
Installing UBUNTU 12.04 x64
XBMC to be installed on top

I should note that this is my first RAID5 attempt.

---

### Post by darkod on 2012-07-06
It's not a direct answer but I think worth considering.

You are planning to run only ubuntu on this, right? In that case, the linux software raid works much better than the bios fakeraid.
I would go into the bios raid again, destroy the array, go into bios and switch back the RAID mode to AHCI.

After that boot the live cd in live mode, and just in case, delete any meta data remains of the fakeraid with:
sudo dmraid -E -r /dev/sda

Do that for all four disks using the correct /dev/sdX name. If it asks you to confirm removal, there was still meta data remains, remove them.

After that use the Alternate CD and install with software raid.

Since the disks are 3TB they will need to have GPT partition table, make sure they do. You can easily make gpt table with parted or Gparted depending what's easier for you.

Also, one more thought. Since this will be a server machine, have you considered the Server version? (you only mentioned the standard and alternate CDs in your post). You are avoiding the server version because of no-GUI?

---

### Post by macsli1 on 2012-07-09
> **darkod said:**
> You are planning to run only ubuntu on this, right?
 ---
...use the Alternate CD and install with software raid.
 ---
Since this will be a server machine, have you considered the Server version? (you only mentioned the standard and alternate CDs in your post). You are avoiding the server version because of no-GUI?

Yes and no...
My plan was to create a Media Center / Storage Server for the family pictures, movies, etc.  I'm connecting this computer to my TV & Stereo so I can run Xbox Media Center ontop of ubuntu.:popcorn:
 ---
I was considering this for a bit but was avoiding it because I figured if at some point for some random reason I needed to install another OS, I'd have to end up adding another drive.  I guess it's just best sticking with ubuntu and will give this method a wirl.
 ---
I could deal without having a GUI for ubuntu, but since I'm going to have this connected to a TV anyway, I figured I'd add a GUI for convience of my other famly members should they need to access their files.  I haven't looked too much into XBMC's UI so I don't know yet if it's worth it to take this route.  Do you feel there would be a particular advantage to going without the GUI in my situation?

---

### Post by darkod on 2012-07-09
You would have to investigate in details all the roles you want it to perform.

But here is my logic:
1. Any server, even a small home storage server, has the function to provide a service and thus can rarely be dual boot. Further more, it's usually a small headless box stuck in some corner. You wouldn't have a monitor and a keyboard connected so you can select to boot one OS or the other.
2. Also, the TV and similar devices will usually access the media with it's own tools, hence there will be no one sitting and working on it. I don't see a point of a GUI in that case, if you are OK with the CLI.

I have a small HP Proliant Microserver stuck in a corner headless, connected to the LAN. It's running only Samba and Twonky (and of course SSH).
My Samsung TV can read the twonky media with its media player.
The computers open the Samba shares as they would any network storage.
That's it, nothing much to it.

I am not sure if your Xbox role needs something, I don't own one. :)

But I guess you can do all server roles you want using SSH and the CLI. Since you confirmed you are OK with the CLI the only reason to have a GUI is if someone is actually sitting down working on it regularly (the family members). Do you plan that?

At the end of the day, install what ever you need to install so that this server works the way you plan it. If that means GUI, no problem.

I would still install the Server version instead of the Desktop/Alternate because it's smaller and more efficient. And then add the GUI of your liking.

---

### Post by macsli1 on 2012-07-09
> **darkod said:**
>   I am not sure if your Xbox role needs something, I don't own one. 

I believe your thinking that I'm connecting this directly to my  Xbox...  Actually I won't be.
XBMC is a program originally written as a hack for the  original Xbox game console way back in 03... Since has been ported to  all major OSes.  Check it out: [xbmc.org/about]("http://xbmc.org/about/") 
...So what I'm really setting up a home theater PC with a server inside because my TV doesn't have any networking capabilities, but it does have a VGA port.

Little off topic...  How does the Samsung fair at handeling different codecs?  I've run into problems with my gaming console handling my movies and was getting frustrated (hence why I'm setting up XBMC).

---

### Post by darkod on 2012-07-09
I am not someone who uses 100 different codecs. My Samsung is UE32C5100, a fairly low level model even when I bought it 18 months ago since I was on a budget. Even then it wasn't the "latest and greatest". :)
But I paid attention in the spec to have ethernet port and support DLNA (for Twonky).

I use it with standard avi DivX and mkv for the HD movies. I am not sure if it's related to Twonky, or the Samsung model, or the combination of both, but I have noticed it displays a not supported file message if the audio codec inside the mkv container is DTS or even AC3 I think. With AAC it works fine. But since I'm not making big fuss over that I haven't taken the time to investigate further and see if that can be sorted out.

For the price I paid for it, I am very happy with it.

If you need more info I am happy to provide it, as long as I know where to find it. :)

---

