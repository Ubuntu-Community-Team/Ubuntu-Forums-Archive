---
title: "Gutsy Live CD won't boot"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Lothas on 2007-10-20
Hi, I just downloaded and burnt the Gutsy ISO into a DVD. Now I'm trying to boot and install it but when I get to the options screen, I can't use any of the options but "Boot from local hard disk". I tried letting the timeout get to 0s but it didn't do anything. Any ideas?

If I wait long enough, after I press enter on the first options, I get a message from the Booter saying something about /casper/"something".

---

### Post by Lothas on 2007-10-20
More specs:
The message being displayed is "Boot Loader: /casper/vmlinuz/" or "Boot Loader: /install/mt86plus/". All I can do is press ok... :(

---

### Post by Lothas on 2007-10-20
bump :$

---

### Post by Lothas on 2007-10-20
Anyone having the same problem?

---

### Post by SunnyRabbiera on 2007-10-20
did you check if the disk is a bad burn?

---

### Post by Lothas on 2007-10-20
I tried burning the ISO twice (both times to a DVD), at different speeds and still no luck. I also tried it on my friend's PC and it didn't work there either. I guess it might be a broken ISO file...

---

### Post by lonesomecrow on 2007-10-20
I have the same issue but only when booting from the amd64 version, the i386 version works fine for me! I want the amd64 version because is the only platform that there's x-fi drivers for!

---

### Post by eph1973 on 2007-10-20
If you go to the terminal and go to the directory where your .iso file is, and enter the following:
```
md5sum ubuntu-7.10-desktop-amd64.iso
```or, if you have the 32 bit version:
```
md5sum ubuntu-7.10-desktop-i386.iso
```Then, verify that number against the number listed on [this page]("https://help.ubuntu.com/community/UbuntuHashes")

If they match, the downloaded .iso is good.

I made a Perl script to check the CD files after the .iso was burned. Open a text editor and copy and paste this script, save it as, say chkggbrn. If you have multiple CD-ROM or DVD drives, or mount it in an odd place, you may have to verify the path to your cd-rom drive:
```

#!/usr/bin/perl -w

use strict;

my @failed_checksums;
my $path_to_cdrom = "/media/cdrom";
my $file_to_read = "$path_to_cdrom" . "/md5sum.txt";

open FILE, "<$file_to_read" or die "Could not open $file_to_read: $!\n";

while(<FILE>){
  my $md5sum;
  my $file_to_checksum;
  my $checksum_result;
  my $md5_result;
  /\s*\./;
  $md5sum = "$`";
  $file_to_checksum = "$path_to_cdrom" . "$'";
  $md5_result = `md5sum $file_to_checksum`;
  $checksum_result = $& if($md5_result =~ /^[0-9a-f]+/);
  if($checksum_result ne $md5sum){
    print "$file_to_checksum failed checksum!\n";
    push(@failed_checksums, $file_to_checksum);
  } else {
    print "$file_to_checksum passed checksum.\n";
  }
}
if(@failed_checksums){
  print "The following files failed their checksum: \n";
  print "$_\n" for @failed_checksums;
} else {
  print "All files passed checksum.\n";
}

```After saving the above script, in your terminal, type:
```
chmod a+x chkggbrn
```Obviously, if you named it something other than chkggbrn, use that name.
Then just type:
```
./chkggbrn
```And it will run. It may pause at about the third file for a minute or so while it runs the checksum, but then it will proceed right through all the different files to check. If any fail their checksum, then your burn is no good.

If both checksums turn out good, and you still have problems, then the problem is probably not with bad data on either the burn or the .iso file.

---

### Post by lonesomecrow on 2007-10-21
Did the checksum, both md5sum numbers match, but I remember getting a burn error with the first cd I did that ended up useless, so redid it, burn was completed and still wont work, I was reading here that when you burn those ISO's it must be at a speed of 4X, but the CD/DVD Creator program does not allow to change that speed, so I think that even though the CD/DVD Creator burn the ISO right, it is not good if it burned it at the drives maximum speed???? just wanna get this out of the way

---

### Post by SquishyMarbles on 2007-10-21
I think I had the same problem as you are describing.  I believe that you have to hit F6, and change "splash" to "nosplash".  I believe that this is a problem may be limited to the amd64 version.

---

### Post by eph1973 on 2007-10-21
When you install the CD, just close the CD/DVD burner box that comes up.  Instead, go to your file manager where the .iso file is, right click on it, then choose write to disk.  On that dialog box, switch the burn speed from maximum possible to the 4.7 or whatever the lowest one ends up being for your machine.  Then let that burn out.  It should take 20 minutes or so.

---

### Post by Lothas on 2007-10-23
Well... I downloaded the ISO again and now I'm writing from Gutsy! Now it's time to tend to all those other Gutsy issues :(

If only I remembered all the steps that I went through with Feisty...

---

