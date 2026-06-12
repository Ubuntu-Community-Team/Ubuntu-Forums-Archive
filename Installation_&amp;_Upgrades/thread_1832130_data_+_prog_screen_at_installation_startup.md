---
title: "data + prog screen at installation startup"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by hfelton on 2011-08-24
this is a breakout/copy-post from another thread i tried to hijack...  sorry...

-----------------

My -severe- installation problem is probably hardware related, but i am at a loss on how to proceed at debugging...

Symptom: during the install-screen of Ubuntu-SERVER-10.04.2-LTS, i see  the -normal- options (white letters on black background) - but i ALSO  see something in the upper-left-corner of the screen...

the upper left corner of the screen writes (inside a -box-) two  columns...  the first column is labelled 'data', the second is labelled  'prog'...  the data column has rows consisting of hex-stuff, as does the  prog column...  below that, there is a box that says err e and then  >>Vietnam<< - which is just bizarre...

here is my ascii-attempt at drawing:
_______________________________
! data               !  prog              !
! 76:  58123. 4  !  5:    45b7. 5  !
! 77:  58141. 4  !  6:    6bed.65  !
 ! 78:  58161. 4  !  7:   9f384. a  !
 ! 79:  5817d. 4  !  8:       7. 1  !
! 7a:  581a7. 4  !  9:       2. 1  !
! 7b:  581ca. 4  !  a:    6bgf.55  !
! 7c:  581eb. 4  !  b:    6bea.15  !
! 7d:  58209. 4  !  c:    6be1. 5  !
______________________________
! err:  e                                    !
! ip 5174:   4.7                          !
!  >>Vietnam<<                        !
________________________________


this pc is an old (2002) VIA mobo with a 1100Mhz celeron...

ive tried changing the dram (100 and 133 from 64m to 512m sticks)...
ive tried bypassing the onboard vga port with a pci-vga card...
ive swapped ps2-keyboards and mice...
ive tried various incarnations of details on the award-bios to see
 about possibly bypassing some of the issues im having...

im just at a loss as to what this symptom means...

unimportant, but i have tried many-other distributions and the
ubuntu-server is the one that seems to make the most-progress
in this situation...  unfortunately, i cannot use the arrow keys to
successfully scroll down to the -test-memory- option of the install...
it turns out that i am only allowed 5 presses on the keyboard arrows
before the whole system locks-up...  (the fourth press changes the
data/prog info, and the 5th press gives me a boot: prompt but
does not accept any further input)

my guess ?  bad mobo somewhere...  whats odd is that back in
2003, id been running linux on it successfully up until a year or
two ago (i think i had rh9 and then centos 5.4 was on the hdd
when i booted up a few days ago to try an ubuntu-distribution)...
i had been swapping out hdd and managed to screw up the LVM
somehow so i was trying to start-over with ubuntu...

anyways, i appreciate any help that yall can provide...  especially
if you can just say something like " oh, that data/prog stuff means
that the processor/mobo/??? is broken - so trash the system " ...  :smile:

sincerely, harold.

btw - ive tried google and searching these forums, but am unable
to come up with some useful keywords that describes my situation...

---

