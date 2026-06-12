---
title: "ALSA, GDM problems after upgrading to Dapper"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by batkins on 2006-06-18
I upgraded to Dapper from Breezy last week (by updating my sources.lst and then running apt-get dist-upgrade).  The upgrade seemed to work fine, but now I'm having some problems:

  - GDM can only log me into the xterm failsafe session, even for freshly-created users.  Once in the failsafe session, I can run "gnome-session" from this failsafe xterm to get a working GNOME environment, but GDM can't seem to do it on its own.
  - ALSA no longer recognizes my sound card (an old Creative SB Live!).  The card shows up in lspci, but no programs that use ALSA will believe that there's a sound card attached to my computer.  If I modprobe snd-emu10k1, then the GNOME volume control will show my card in the device list and even let me adjust volume settings, but other programs still give a "no such device" error.

I've tried reinstalling gnome, gnome-session, gdm - all to no avail.  As I mentioned, even brand-new users can't get into gdm, so this leads me to believe the problem is not in my personal configuration of GNOME.  I've also tried deleting .gnome2/session and .ICEAuthority, and trying to log in with a new user with a completely blank home directory.  No dice.

Here is the message I get when logging into a regular GNOME session:

> 
I could not start your session and so I have started the failsafe xterm session. Windows have focus only if you have your cursor above them. To get out of this mode type 'exit' in the window in the upper left corner.


Here is the contents of .xsession-errors:

> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bill"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator


Here's what lspci says:

> 
% lspci | grep -i audio
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)


Here are the ALSA modules I have loaded:

> 
% lsmod | grep snd
snd_emu10k1_synth       7520  0
snd_emux_synth         36032  1 snd_emu10k1_synth
snd_seq_virmidi         7168  1 snd_emux_synth
snd_seq_midi_emul       7584  1 snd_emux_synth
snd_seq_midi            9088  0
snd_seq_midi_event      6848  2 snd_seq_virmidi,snd_seq_midi
snd_seq                50736  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           118340  1 snd_emu10k1_synth
snd_rawmidi            24704  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8460  6 snd_emu10k1_synth,snd_emux_synth,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         83932  1 snd_emu10k1
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10600  2 snd_emu10k1,snd_pcm
snd_util_mem            4448  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8896  2 snd_emux_synth,snd_emu10k1
snd                    54884  12 snd_emux_synth,snd_seq_virmidi,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9600  4 snd,emu10k1,sound


Here's alsamixer's reaction:

> 
% sudo alsamixer                                                                                            
alsamixer: function snd_ctl_open failed for default: No such device


Any help would be much, much, much appreciated.  I've been trying to fix this up for three days now and I'm pretty baffled.

> 
Ubuntu 6.06
% uname -a
Linux lambda 2.6.12-10-686 #1 Sat Mar 11 16:22:51 UTC 2006 i686 GNU/Linux


---

### Post by batkins on 2006-06-23
bump?

---

### Post by Othersider on 2006-06-23
I am having the exact same sound problems, except:

> 
$ lspci | grep -i audio
0000:05:04.0 Multimedia audio controller: Creative Labs SB Audigy LS


Any help would be great.

---

### Post by Alex1770 on 2006-08-31
I have the same problem with my sound card not being recognised after a
breezy->dapper upgrade.

lspci shows (amongst other lines)
0000:01:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:01:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)

(those stupid smilies should say '8' followed by ')')

and

cat /proc/asound/cards 
shows

0 [nForce2        ]: NFORCE - NVidia nForce2
                     NVidia nForce2 with ALC650E at 0xeb001000, irq 177
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10


nForce2 is the motherboard's (integrated) sound, and I have no idea what
UART is.

If you boot up using the old kernel (but same new Dapper everythnig else) then the SB sound card *is* recognised, which makes it look like there
is a problem with the new kernel (2.6.15-26-k7).

---

### Post by batkins on 2006-08-31
I finally solved this issue: [http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore/](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore/)

---

