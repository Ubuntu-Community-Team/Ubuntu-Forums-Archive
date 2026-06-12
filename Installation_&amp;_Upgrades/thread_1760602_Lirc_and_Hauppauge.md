---
title: "Lirc and Hauppauge"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by Kalf on 2011-05-17
Hello! I'm quite new to linux and Ubuntu. But I've tried it before. But now, I've run in to some problems with my Lirc settings for my remote. I need a remote because i will run my computer as a HTPC.

Info about my system:
Ubuntu 10.04 LTS
Hauppauge WinTV-NOVA-T-PCI
Hauppauge A415-WPG-WE Remote

Image of the remote:
[IMG]http://techgage.com/reviews/hauppauge/wintv_pvr350/hauppauge_350_8_thumb.jpg[/IMG]

My problem is that lirc does not recognize all the buttons of the remote. To test this I'm using the camand:  *irw*

When I've installed Lirc I've choosed Hauppage Nova-t 500. But after som time googeling i've found this "keymap": [http://lircconfig.commandir.com/lircd.conf/?viewremote=1273](http://lircconfig.commandir.com/lircd.conf/?viewremote=1273)
Ive pasted that into */etc/lirc/lircd.conf* so my lircd.conf looks like below:

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.



#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#


begin remote
  name            Hauppauge
  bits            16
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             403983
  pre_data_bits   16
  pre_data        0x1

  begin codes
       TV              0x0179
       Videos          0x0189
       Music           0x0188
       Pictures        0x00E2
       Radio           0x0181
       Guide           0x016D
       Off             0x0074
       Go              0x0162
       Up              0x0067
       Down            0x006C
       Left            0x0069
       Right           0x006A
       Ok              0x0160
       Menu            0x008B
       Back/Exit       0x009E
       Vol+            0x0073
       Vol-            0x0072
       PrevCh          0x016B
       Mute            0x0071
       Ch+             0x0192
       Ch-             0x0193
       Stop            0x0080
       Record          0x00A7
       Rew             0x00A8
       Play            0x00CF
       FFW             0x00D0
       Pause           0x0077
       Replay          0x0195
       Skip            0x0197
       1               0x0002
       2               0x0003
       3               0x0004
       4               0x0005
       5               0x0006
       6               0x0007
       7               0x0008
       8               0x0009
       9               0x000A
       Star            0x0037
       0               0x000B
       Char            0x0029
       Red             0x018E
       Green           0x018F
       Yellow          0x0190
       Blue            0x0191

  end codes

end remote
```This is the result of *irw* when I press the buttons of the remote from the top left and starting to work my way downwards:
```
0000000000010074 00 Off Hauppauge
0000000000010179 00 TV Hauppauge
0000000000010189 00 Videos Hauppauge
0000000000010188 00 Music Hauppauge
000000000001016d 00 Guide Hauppauge
0000000000010067 00 Up Hauppauge
0000000000010181 00 Radio Hauppauge
0000000000010069 00 Left Hauppauge
000000000001006a 00 Right Hauppauge
000000000001006c 00 Down Hauppauge
000000000001008b 00 Menu Hauppauge
0000000000010073 00 Vol+ Hauppauge
0000000000010192 00 Ch+ Hauppauge
0000000000010072 00 Vol- Hauppauge
0000000000010071 00 Mute Hauppauge
0000000000010193 00 Ch- Hauppauge
00000000000100a7 00 Record Hauppauge
0000000000010080 00 Stop Hauppauge
00000000000100a8 00 Rew Hauppauge
00000000000100cf 00 Play Hauppauge
00000000000100d0 00 FFW Hauppauge
0000000000010077 00 Pause Hauppauge
0000000000010002 00 1 Hauppauge
0000000000010003 00 2 Hauppauge
0000000000010004 00 3 Hauppauge
0000000000010005 00 4 Hauppauge
0000000000010006 00 5 Hauppauge
0000000000010007 00 6 Hauppauge
0000000000010008 00 7 Hauppauge
0000000000010009 00 8 Hauppauge
000000000001000a 00 9 Hauppauge
000000000001000b 00 0 Hauppauge
000000000001018e 00 Red Hauppauge
000000000001018f 00 Green Hauppauge
0000000000010190 00 Yellow Hauppauge
0000000000010191 00 Blue Hauppauge

```In other word, the following keys does not work on the remote:

Go
Pictures
Guide
Ok
Back/Exit
PrevCh
Replay
Skip
Star
Char

Since I'm new the the Linux, and Ubuntu Scene I'm not sure where to begin. Any Ideas?

mvh. Kalf

---

