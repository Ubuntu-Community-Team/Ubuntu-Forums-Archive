---
title: "Patching"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by NetSlider on 2010-06-24
Ok, first and foremost, I'm not only a complete noobie to Linux but computers are not something I even studied; I just find them interesting and I found community people are very nice and helpful. So, this being said, here is my problem. 

I'm trying to patch my laptop's internal mic. Without getting into too much details (if interested here is the link to the project that I found []http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone](]http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone)]) Now, I have no idea how to patch so I spend the last two days reading load of info on it and now I hit the brick wall with the dirs. The patch inside looks like this:


[B]From 198d791792a15c8128dee7cc02c03eb8107921ee Mon Sep 17 00:00:00 2001
From: Jason A. Donenfeld <Jason@zx2c4.com>
Date: Wed, 10 Feb 2010 18:49:16 -0500
Subject: [PATCH] Force ALC269 to use internal microphone on VPCF11.


Signed-off-by: Jason A. Donenfeld <Jason@zx2c4.com>
---
 sound/pci/hda/patch_realtek.c |    4 ++--
 1 files changed, 2 insertions(+), 2 deletions(-)

diff --git a/sound/pci/hda/patch_realtek.c b/sound/pci/hda/patch_realtek.c
index da34095..e62c5a7 100644
--- a/sound/pci/hda/patch_realtek.c
+++ b/sound/pci/hda/patch_realtek.c
@@ -13119,11 +13119,11 @@ static int patch_alc268(struct hda_codec *codec)
 
 static hda_nid_t alc269_adc_nids[1] = {
 	/* ADC1 */
-	0x08,
+	0x11,
 };
 
 static hda_nid_t alc269_capsrc_nids[1] = {
-	0x23,
+	0x22,
 };
 
 /* NOTE: ADC2 (0x07) is connected from a recording *MIXER* (0x24),
-- 
1.6.6.1[/B]

My question is, when I run *patch -p0 /usr/src/picpatch/enable-internal-microphone.patch* nothing happens. I've tried changing the dirs inside the patch itself and still nothing happens (I mean once i press enter ssh goes to another line but without the whole *root@netslider:~#*; sorry for the lack of term knowledge).
So, I think that the prob is that the patch does not specify the dirs where to apply the patch, but when I try changing it - same thing. The patch provider just says "apply it to your kernel, and rebuild, and install" and I have no idea what it means. I'm open to learning linux and I understand that in order to learn one must read a lot of things on line, but at this point I'm going insane. 
PLEASE HELP!!! I'M GOING INSANE BUT I'M NOT GOING GIVE UP USING UBUNTU JUST BECAUSE OF THE MIC!!! I'm already about 50/50 on Win7 and Ubuntu and would like to get to the point where i use Win only for work soft. 
THANKS in advance and any help would be great.

---

