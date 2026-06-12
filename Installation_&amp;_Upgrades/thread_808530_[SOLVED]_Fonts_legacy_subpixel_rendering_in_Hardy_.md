---
title: "[SOLVED] Fonts: legacy subpixel rendering in Hardy Heron?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Faerine on 2008-05-26
I have mostly used Dapper so far. The new font subpixel rendering in Gutsy Gibbon and now in Hardy Heron doesn't work well for my eyes at all. I have tried all combinations in System - Preferences - Appearance - Fonts - Details, as well as separately enabling autohinting (and then trying the combinations again). 

I want to, in Hardy, revert to the subpixel rendering used in Dapper (used probably in Feisty, too). I was having difficulties doing that in Gutsy Gibbon, and from reading other threads I see that there have been bugs in that respect that are supposed to have been fixed in Hardy Heron. However, I can't revert in Hardy, either.

I added:

<?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- Use the older subpixel rendering: LCDFILTER legacy -->
    <edit name="lcdfilter" mode="assign"><const>legacy</const></edit>
</fontconfig>

in /etc/fonts/local.conf, but nothing changes. Thanks for your advice.

---

### Post by Faerine on 2008-05-26
I found an answer to my question here: [http://johan.kiviniemi.name/blag/2008/01/12/ubuntu-hardy-fonts/](http://johan.kiviniemi.name/blag/2008/01/12/ubuntu-hardy-fonts/) . Many thanks to the person who posted this.

---

