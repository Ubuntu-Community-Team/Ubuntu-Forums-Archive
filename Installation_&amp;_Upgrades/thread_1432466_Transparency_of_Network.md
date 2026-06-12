---
title: "Transparency of Network"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by Xeneon on 2010-03-17
I am currently looking for a solution to my networking, server & desktop arrangements on my computers to make network folders transparent, prevent having multiple copies of the same files on different computers on my network & allow more efficient use of my computers.

I guess I'll start with describing my current computer/network environment. I currently have 5 computers actively using my home network. One computer in my lounge room is always on. It is running windows XP & is used for File Sharing, a Diablo II BattleNet server & a media centre as it is plugged into my TV. All my files (videos, music, work, personal, etc...) are stored on this computer. This computer also runs a VNC that I can access over the local network & over the Internet.
I have 2 personal computers, both running Ubuntu, A Desktop computer & a Laptop. I keep all my files on the server computer to try and keep things organised and avoid having multiple copies of files I'm working on. The biggest problem I have is that most programs cant access the network folders, so to work on a file I need to copy it over to a local folder & copy it back when I'm done. I also take my laptop with me to work & university and if I want to work on a file there I need to remember to copy the files in advance.
The other 2 computers are my brothers (windows) & a neighbour (mac). They use the network for Internet access & access the file sharing for videos/music.

What I want the system to be able to do is this:


Central computer to act pretty much the same way it does now. I'm thinking of swapping it to Ubuntu tho rather then windows so I need to know if it would be better to run server or desktop release of Ubuntu & what programs to install/use so it can:
1-a) Give full access to users on certain files/folders, give read access to users on certain files/folders, have folders that only I can read/write to on my computers.
1-b) Still act as a Media Centre for my TV, with IR remote control (I have a harmony remote) 
1-c) run my DII BNet server. Im fairly confident I'll be able to get this to work using wine.
1-d) run a VNC



I want my desktop & laptop computer to:
2-a) think that those files stored on the network are in local files (I think I can use CIFS/SMBmount to mount the folders on boot up but don't know the difference/how to do it)
2-b) the laptop should be able to do this over the Internet so I can still access this when not at home. I know how to set up the router to do this, but I want to do this without using a VPN so would I need to use something like an SSH or FTP program on the server to ensure security. Can these be mounted in a similar fashion to shared folders?

Any advice or suggestions would be really handy. Thanks

---

