---
title: "GRUB appearence settings no longer work"
date: 2021-03-03
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2021-03-03
This weekend, I finally got around to doing a clean install of Ubuntu 20.4 -- and went through my usual customizations, one of which was using GRUB-Customizer to set appearance options: resolution, background image, text colors.  This has always worked in the past, year after year.

But when I rebooted, although the screen resolution changed, the background was still black and the default text colors were there.

I thought this might be a problem with GRUB-Customizer not setting the proper values, but I opened the default GRUB config file and confirmed the following values were set properly:
GRUB_MENU_PICTURE
GRUB_COLOR_NORMAL
GRUB_COLOR_HIGHLIGHT

I had read the release notes for Ubuntu 20.04 and they mentioned a new GRUB splash screen, but I am not getting that.

Instead, I get the default text screen with the default colors.

So now, unless this is a known bug, I don't know what to do to fix it.

---

### Post by Paddy Landau on 2021-03-05
I am also interested in this question.

**GRUB_COLOR_NORMAL & GRUB_COLOR_HIGHLIGHT**

These appear to no longer work. The correct way to change these, I understand, is to create a Grub theme, and reference that theme with the parameter GRUB_THEME.

I don't know how to create a Grub theme. Depending on why you want it, it might be too much work for something that appears only briefly during startup.

**GRUB_MENU_PICTURE**

If you copy your image to /boot/grub, Grub will automatically pull it in; you don't need GRUB_MENU_PICTURE. (I don't know what Grub does if that folder has multiple images.)

However, if the image is saved elsewhere, you do need that parameter. Put quotation marks around the image name. But, be sure that the image is available to Grub at boot time. For example, my disk is fully encrypted, so I cannot use an image that's placed in (say) /home.

Further, Grub supports only PNG images and 256-colour JPG images. If it's JPG and isn't 256-colour, Grub will ignore it. Thus, save the image either as PNG or as 256-colour JPG.

In my case, I didn't need to use Grub Customizer at all; I just copied my PNG image to /boot/grub.

---

### Post by Mark Phelps on 2021-03-08
@Paddy -- thanks for your response

I should have provided more details -- as this is a PNG file (as I had used it in previous Ubuntu releases, including 19.10) and it is saved in /boot/grub.

So basically, it SHOULD be working -- but is not.

---

