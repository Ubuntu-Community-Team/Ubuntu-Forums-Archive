---
title: "Feisty Fawn install on 256Mb machine stuck"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by hardmath on 2007-06-10
I downloaded and verified a Feisty Fawn Live CD (desktop i386), and tried to use it for installation on a PC with five year old hardware and 256 Mbytes of memory, the listed minimum for installation using the Live CD.

I found that the install consistently hung on partitioning the hard drive at 15% completed, a phenomenon noted by others.  The Ubuntu directions say the install may slow and "appear to hang" (my mouse became unresponsive), but I did let the process run for 48 hours with no progress.  So I think it fair to say the install will sometimes get stuck here with 256Mbytes of memory.

The two main workarounds suggested are to use the alternate CD/text-based installer or to add more memory.  I decided to at least try the alternate CD (again Feisty Fawn, i386).

I ran into minor problems verifying the CD.  I downloaded the ISO image from two mirrors, which both seem intact according to the md5sum generated on the .iso files, and burned them on two different Windows machines (using Alex Feinman's CD Recording Wizard at 4x on one, and InfraRecorder at 8x on the other).

Both alternate CD's then report "slight" md5sum.txt checksum descrepancies (checked using the cygwin bash shell's md5sum utility), as summarized by:

md5sum: WARNING: 6 of 1526 listed files could not be read
md5sum: WARNING: 1 of 1520 computed checksums did NOT match

Actually using the CD's, I'm able to get through the "base package" installation (past the drive partitioning in particular), but it fails during the next step ("select and configure packages") with just a simple message to that effect.

Since the disk partitioning under the alternate CD succeeded, I hoped that perhaps this might allow the Live CD installation to get past that point.  But if there is a workaround along those lines, I did not immediately find it.

I read in another post that one person, having a similar experience with the alternate CD, was successful in (as I understood it) stopping with the base package installation and resuming the process somehow using only command line stuff to complete the installation.  

Any suggestions? Or should I bite the bullet and add more memory to this machine?  I last installed Dapper Drake (6.06), and none of these problems cropped up.  But then I never had to resort to the alternate CD or wrangle with minimum memory limitations.

regards, hardmath

---

### Post by merlinus on 2007-06-10
Clearly the problem is with your cd.

Trying to install from a disk that has errors will undoubtedly lead to untoward complications.

Try burning it at 1x.

Good luck!

-merlin

---

### Post by hardmath on 2007-06-10
merlinus wrote:

> Clearly the problem is with your cd.

> Trying to install from a disk that has errors
> will undoubtedly lead to untoward complications.

> Try burning it at 1x.

> Good luck!

Thanks, but I think the fact that identical md5sum errors
occurred on more than one CD (using two mirrors, two
PCs, and two burner programs) make either the alternate
CD ISO file the source of those errors, or conceivably
some quirk of the cygwin md5sum implementation.  I did
try burning the CDs at 9x, 8x, and finally 4x without any
change in the md5sum.txt checksum behavior.  For the
sake of submitting a bug report, however, I will take your
advice and burn another at 1x.

But I did have good luck today!

hardmath wrote:

> Since the disk partitioning under the alternate CD
> succeeded, I hoped that perhaps this might allow the
> Live CD installation to get past that point. But if there
> is a workaround along those lines, I did not immediately
> find it.

I left the Live CD install running overnight, and when I
went back to look around noon, that installation had 
completed!  Everything is working now.  My guess is
that having the partitioning step completed by the
alternate CD install did improve the initial conditions
for the Live CD install.

regards, hm

---

### Post by hardmath on 2007-06-10
hardmath wrote:

> Thanks, but I think the fact that identical md5sum errors
> occurred on more than one CD (using two mirrors, two
> PCs, and two burner programs) make either the alternate
> CD ISO file the source of those errors, or conceivably
> some quirk of the cygwin md5sum implementation.

I checked all three alternate i386 CDs I burned so far,
using the Linux md5sum utility rather than cygwin's,
and there were no errors or warnings.  So I think the
story on that topic is that cygwin's checks are pickier
than the Linux implementation.

--hm

---

### Post by Jim McKnight on 2007-07-03
> **hardmath said:**
> I downloaded and verified a Feisty Fawn Live CD (desktop i386), and tried to use it for installation on a PC with five year old hardware and 256 Mbytes of memory, the listed minimum for installation using the Live CD.

I found that the install consistently hung on partitioning the hard drive at 15% completed, a phenomenon noted by others.  The Ubuntu directions say the install may slow and "appear to hang" (my mouse became unresponsive), but I did let the process run for 48 hours with no progress.  So I think it fair to say the install will sometimes get stuck here with 256Mbytes of memory.

The two main workarounds suggested are to use the alternate CD/text-based installer or to add more memory.  I decided to at least try the alternate CD (again Feisty Fawn, i386).

I ran into minor problems verifying the CD.  I downloaded the ISO image from two mirrors, which both seem intact according to the md5sum generated on the .iso files, and burned them on two different Windows machines (using Alex Feinman's CD Recording Wizard at 4x on one, and InfraRecorder at 8x on the other).

Both alternate CD's then report "slight" md5sum.txt checksum descrepancies (checked using the cygwin bash shell's md5sum utility), as summarized by:

md5sum: WARNING: 6 of 1526 listed files could not be read
md5sum: WARNING: 1 of 1520 computed checksums did NOT match

Actually using the CD's, I'm able to get through the "base package" installation (past the drive partitioning in particular), but it fails during the next step ("select and configure packages") with just a simple message to that effect.

Since the disk partitioning under the alternate CD succeeded, I hoped that perhaps this might allow the Live CD installation to get past that point.  But if there is a workaround along those lines, I did not immediately find it.

I read in another post that one person, having a similar experience with the alternate CD, was successful in (as I understood it) stopping with the base package installation and resuming the process somehow using only command line stuff to complete the installation.  

Any suggestions? Or should I bite the bullet and add more memory to this machine?  I last installed Dapper Drake (6.06), and none of these problems cropped up.  But then I never had to resort to the alternate CD or wrangle with minimum memory limitations.

regards, hardmath
I fixed an identical hang (at 15%) while trying to install Ubuntu Feisty Fawn in a multiboot environment and with manual partioning.
  
I upgraded my RAM from 256mb to 768mb and then everything went fine. I think the 256mb requirement is probably for a vanilla install single boot. 

This was on a GQ (Fry's) PC with AMD Sempron processor. I had read on some PS3 forums that adding RAM had fixed this failure on PS3 installs, so I tried it on my PC.

---

