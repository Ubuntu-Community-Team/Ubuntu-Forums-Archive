---
title: "CD/DVD doesn't unmount after ejecting"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-04-25
I've noticed over the past few days that when I press the eject button on my dvd drive (physical button) that my computer will sometimes freeze until I press it 3-4 times until it finally ejects.

When the disc does eject, it will leave the icon mounted on my desktop. Loading discs from then on causes problems and they won't mount until I actually right-click and click unmount for the disc that isn't even there.

Anyone else seen this?

---

### Post by florus on 2010-04-25
Unmount the drive before ejecting. This ensures that the drive is not reading/writing when you eject the disc.

---

### Post by kyleabaker on 2010-04-25
> **florus said:**
> Unmount the drive before ejecting. This ensures that the drive is not reading/writing when you eject the disc.

As simple as that is (which I now do anyway), its an unintuitive extra step compared to other OS's and besides that...it used to work as expected. With 10.04 being LTS it should work as expected. Any idea what I need to file this under on Launchpad?

---

### Post by florus on 2010-04-25
Sorry, I cannot agree with you. I always unmount drives, partitions, and other computers when I have finished accessing them. Tidy, logical and safe.

---

### Post by kyleabaker on 2010-04-25
> **florus said:**
> Sorry, I cannot agree with you. I always unmount drives, partitions, and other computers when I have finished accessing them. Tidy, logical and safe.

So you expect new converts from Windows and Mac to just do this rather than have yet another OS that is smart enough to unmount on eject? With Ubuntu trying to be for Human beings and not robots, it makes sense for them to make this work out of the box on its own without problems. Your extra step may be natural to you, but in the scheme of things its quite out of the way.

---

### Post by florus on 2010-04-25
You could be right - it is a long time since I used windows. Personally I find Ubuntu far more intuitive than windows. I did try Vista briefly, but could not make head nor tail of it.

---

### Post by mikeyrb on 2010-04-25
Can you give me the output of the cdrom_id app when your drive is empty?

# /lib/udev/cdrom_id -d /dev/sr0

Where /dev/sr0 is your dvd drive (may be /dev/sr1, etc).  The -d adds debug information.

---

### Post by kyleabaker on 2010-04-26
> **mikeyrb said:**
> Can you give me the output of the cdrom_id app when your drive is empty?

# /lib/udev/cdrom_id -d /dev/sr0

Where /dev/sr0 is your dvd drive (may be /dev/sr1, etc).  The -d adds debug information.

```

kyleabaker@kyleabaker-desktop:~$ /lib/udev/cdrom_id -d /dev/sr0
main: probing: '/dev/sr0'
cd_media_compat: CDROM_DRIVE_STATUS != CDS_DISC_OK
cd_inquiry: INQUIRY: [_NEC    ][DVD+RW ND-1100A ][1.93]
cd_profiles: GET CONFIGURATION: size of features buffer 0x00c8
cd_profiles: GET CONFIGURATION: feature 'profiles', with 6 entries
feature_profiles: profile 0x1b dvd_plus_r
feature_profiles: profile 0x1a dvd_plus_rw
feature_profiles: profile 0x10 dvd_rom
feature_profiles: profile 0x0a <ignored>
feature_profiles: profile 0x09 <ignored>
feature_profiles: profile 0x08 <ignored>
cd_profiles: GET CONFIGURATION: feature 0x0001 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0002 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0003 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0010 <ignored>, with 0x08 bytes
cd_profiles: GET CONFIGURATION: feature 0x001d <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x001e <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x001f <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0020 <ignored>, with 0x0c bytes
cd_profiles: GET CONFIGURATION: feature 0x0021 <ignored>, with 0x08 bytes
cd_profiles: GET CONFIGURATION: feature 0x0023 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0026 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x002a <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002b <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002d <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x002e <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0100 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0103 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0105 <ignored>, with 0x00 bytes
cd_profiles: GET CONFIGURATION: feature 0x0106 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x0107 <ignored>, with 0x04 bytes
cd_profiles: GET CONFIGURATION: feature 0x010a <ignored>, with 0x0c bytes
cd_profiles: no current profile, assuming no media
ID_CDROM=1
ID_CDROM_CD_R=1
ID_CDROM_CD_RW=1
ID_CDROM_DVD=1
ID_CDROM_DVD_PLUS_R=1
ID_CDROM_DVD_PLUS_RW=1
kyleabaker@kyleabaker-desktop:~$

```

As soon as I hit the eject button my system freezes...becomes unresponsive until I hit the eject button 2-3-4 times. This output is taken immediately after the tray opens and the disc is not unmounted and is still present on my desktop.

Hope this helps solve this situation!

---

### Post by mikeyrb on 2010-04-26
Well, that log only tells me that program is not at fault.  I was able to reproduce it on a laptop, and I know there are bug reports in launchpad about this, but I think the last one I saw claimed resolved, not that I think it is.

Anyways, file a bug against nautilus (use app ubuntu-bug) for now; it may be something else is at fault, but unless someone can confirm it's a problem also with kde, assume nautilus.  I will look into it if it's not solved by the end of the week, but the beginning of my week is too busy :)

---

