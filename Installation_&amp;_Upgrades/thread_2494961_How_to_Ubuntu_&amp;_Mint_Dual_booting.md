---
title: "How to Ubuntu &amp; Mint Dual booting"
date: 2024-02-01
forum: Installation &amp; Upgrades
---

### Post by aughey on 2024-02-01
I have a Toshiba C855 laptop which was running Windows 10 alongside Mint 21.1 via grub. I had to use Windows and whatever happened grub ceased working. It would boot straight into windows only. I tried reinstalling Mint via USB but it didnt change. The BIOS is currently set to UEFI mode which only gets me windows.  Changing it to AHCI CSM mode reported No bootable device -- insert boot  disk and press any key. I re installed Mint at this prompt using USB and it now boots mint only in that bios setting and windows in UEFI mode

What I want to do is get rid of Windows completely and dual boot mint and Ubuntu instead. My Toshiba has a 1tb SSD and 16 gigs memory

How do I do this. I have created a USB for Ubuntu 23.10 and have a separate one for Mint 21.3 the latest version

---

### Post by guiverc on 2024-02-01
I have no recent experience with Linux Mint, so I cannot help there.

I'll provide some pointers, that I hope are useful.

Ubuntu 23.10 is available on multiple ISOs that use different installers, and you weren't specific as to which Ubuntu 23.10 product. There is one Ubuntu 23.10 Server ISO that uses the `subiquity` installer, however Ubuntu 23.10 Desktop has two choices; the first uses `ubuntu-desktop-installer` and the second uses `ubiquity`.  I'd expect all three to achieve what you're after without issue (*though as I'm mostly a desktop user, I've more experience with the desktop installer, esp. older `ubiquity` which is what Linux Mint has historically used too - *[https://community.linuxmint.com/software/view/ubiquity](https://community.linuxmint.com/software/view/ubiquity) *though its now deprecated code in Ubuntu*)

What can make a difference is how you write the ISO to your thumb-drive or other installation media. If you use any *reformat* options, you risk creating an system which will only install on certain computers & certain modes (such as only in *legacy/BIOS* mode, or only in *uEFI* etc).  If you write the ISO via a simple clone (*no reformat*), or as documented by Ubuntu for that product/release, it'll boot & install in all of *legacy/BIOS, uEFI and Secure-uEFI* modes correctly.  Thus I'll suggest just follow official docs.

I installed a Ubuntu 22.04 LTS system yesterday as a QA-test install (*Lubuntu 22.04.4 LTS actually, thus it used the `calamares` installer, but installer isn't significant here*) and it was on a system I actually use with my own data.  Part of my testing is to ensure the install didn't corrupt anything of mine; and post-boot all four OSes booted normally.  On that machine I want my Debian *trixie* to own the boot process; however the 22.04.4 re-install caused that to get lost, but I just let it... and correct the situation once I've completed the QA (*Quality Assruance*) tests.  

I'd expect the same with you, ie. just install the system (*Install alongside type of install*), and if you do it correctly, you'll have the option to boot both OSes.  If you want another OS (*like Debian in my last paragraph example*) to have ownership of boot, correct that afterwards. The commands to do this vary on OS, but it's `update-grub` and `grub-install` on Debian & Ubuntu systems (*varying on OpenSuSE, Fedora & others*). By the default the *last* installed OS will control/own the booting (ie. *last paragraph the last install was Ubuntu 22.04.4 thus it took over ownership, I just reverted that manually with two commands*).  *FYI:  Your windows update just likely caused windows to take ownership of boot.. that can be corrected too.*

For specific advice, you'll need to be specific; ie. are you asking about Ubuntu 23.10 Server?  or Ubuntu 23.10 Desktop?  as different installers are involved (*with choices for Desktop*).  The different installers don't change much; however do change how it appears on screen.

---

### Post by aughey on 2024-02-02
Can I simply install Ubuntu 23.10 desktop over the current Windows 10 install followed by Mint 21.3. I previously tried installing Mint directly over a Ubuntu install in the past and it caused errors which meant the system would not boot at all. I forget now exactly what the errors were.

---

### Post by guiverc on 2024-02-02
> **aughey said:**
> Can I simply install Ubuntu 23.10 desktop over the current Windows 10 install followed by Mint 21.3. I previously tried installing Mint directly over a Ubuntu install in the past and it caused errors which meant the system would not boot at all. I forget now exactly what the errors were.

If you use a *Erase disk and install* type of option in installing Ubuntu Desktop; you'll have the maximum success of the install working completely.

Ubuntu  23.10 Desktop offers two download options; one uses the `ubuntu-desktop-installer` installer, the *legacy* ISO being your option which uses the older `ubiquity` installer (*what I provided a link pointing to Linux Mint's copy of it*). This means if you have problems with one, you've got another you can try.

If the ISO is written as documented, it'll have a more than 95% chance of installing correctly; however there are some hardware platforms with *quirks* that were worked around by the OEM in installing the provided windows that may not be catered for, so it's not fool-proof.

Do you have a second machine?  as if one ISO fails to install and the machine thus can't be used to write the other ISO, you need something else to fall back on (*even a borrowed machine such as from family*),  let alone seeking help on support sites like this one.

Grub install failures are a common issue I see; which are least likely with full disk installs, however some BIOS *firmware* settings can prevent normal operation (*firmware is your BIOS and its settings, these are machine specific*), plus how the ISO is written can cause issues here too, but again some devices are not made as per ISO standards (*the quirks the OEMs get around on the initial install of the OS the machine is sold with*)

---

### Post by yancek on 2024-02-03
The information in your first post would indicate you had windows installed UEFI and Mint in Legacy mode on the same hard drive so what you got is expected behavior.

If you do an EFI install of Ubuntu and Mint, the 2nd install will overwrite the EFI files of the first as Mint and some of the other major Ubuntu derivatives also create a directory named ubuntu on the EFI partition rather than using mint, kubuntu, etc.  The 2nd install should update grub and include the first install in the boot menu so install the system you want in control last.  This is applicable if you have one physical drive.

---

