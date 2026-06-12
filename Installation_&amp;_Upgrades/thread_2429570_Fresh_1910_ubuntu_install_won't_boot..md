---
title: "Fresh 1910 ubuntu install won't boot."
date: 2019-10-19
forum: Installation &amp; Upgrades
---

### Post by chris_jones2 on 2019-10-19
I ran the 1910 ubuntu install on a fairly ancient  W700 Thinkpad that already has a bunch of linux systems installed including ubuntu 18.04 LTS and all of them are pretty healthy. 

I used the official ubuntu iso (ubuntu-19.10-desktop-amd64.iso) and everything went without a glitch.

Upon starting the new system the boot process gives out a few messages… relative to the console being intialized… the system's temperature and such… and then stalls after this message:

> linux agpgart interface v0.103random: fast init done

Followed by what looks line a call trace something the kernel might display after a crash.

> tpm_tis_pnp_init … +0xd2/-x100
> pnp_device …
> … etc.
> kernel_init +0xe/0x100

Then after maybe 60 seconds… another familiar message:

> random: crng init done

followed by another (identical?) call trace.

> tpm_tis_pnp_init … +0xd2/-x100
> pnp_device …
> … etc.
> kernel_init +0xe/0x100
> ret_from_fork +0x35/0x40

And then the boot process just hangs there.

If I let it run the same call trace is displayed and it does not go any farther.

I have done numerous linux installs on this and other machines and I have never seen anything quite like this before.

Any suggestions as to what's going on and what I should do next?

Thanks,

CJ





[TABLE="class: cf gJ"]
[TR="class: acZ"]
[TD="class: gF gK"][/TD]
[TD="class: gH bAk"][/TD]
[/TR]
[/TABLE]

---

### Post by Skaperen on 2019-10-19
can you attach a digital photo of the screen?

---

### Post by chris_jones2 on 2019-10-19
Booted this u1910 install again and I took some pictures. But this time the scenario was somewhat different. Apparently the kernel was unable to find the root system (although I had not changed anything) and I was eventually dropped to a shell with an (initramfs): prompt. Some of the pics I took are blurred especially the more useful ones. I'll try running this again tomorrow. This is really weird. Seems the 5.3 kernel doesn't like my (non-UEFI) hardware?  I don't suppose I could download a 19.04 vanilla ubuntu and what happens&#8230;?

---

### Post by Skaperen on 2019-10-20
do you have a specific need for 19.10 instead of 18.04 LTS?  wanting to explore is specific enough.  otherwise i suggest using 18.04 until after 20.04 comes out in spring.  and you could explore in a VM and copy that 19.10 file base into container on the 18.04 host.  that way you could be running the 19.10 packages on a 5.0.0 kernel.

---

### Post by chris_jones2 on 2019-10-20
I don't particularly 'need' 19.10. Made a habit of installing the latest  ubuntu as soon as it's released&#8230; I don't use ubuntu anyway&#8230; I only have  it handy to get a feel of where things are headed with mainstream  GNU/linux&#8230; There are two things that are bothering me. 1. I have  installed all sorts of linux over the years and save silly errors I have  never had a problem like this. smartmon tools tell me that the disk  where 19.10 is installed is basically OK. All the same I don't like the  smell of it and I'm not too happy just forgetting about it. 2. The 20.04  and the kernel that come with it will be built on what I have here.  Hence, unless someone runs into this problem&#8230; or even a completely  different problem with the same root cause&#8230; and it gets fixed before  next April&#8230; the chances are that I will have the same problem with  20.04. I didn't have time to look further into this today but I remember  seeing on the ubuntu.com site a minimal version c. 500MB in size. I'll  give that a try tomorrow writing down everything I do as I go along. If  that also fails to boot in the same manner&#8230; I'll do some research on  what parms should be passed to the 5.3 kernel via grub. Thank you for  your suggestions and I'll update the issue if/when I find something.  CJ.&nbsp;

---

### Post by chris_jones2 on 2019-10-21
Pretty much what I was beginning to suspect&#8230; 

I did a fresh install of the same 19.10 iso on a new partition and it booted fine from the grub 2.04 (?) menu that said install had created. 

Now the problem with this is that apart from the fact that this menu is cluttered with submenus that I have no use for&#8230; I do **not** want my grub stuff to live on this new system that I might choose to nuke any time soon.

So I booted into my debian stable (buster) system&#8230; added a stanza to my /etc/grub.d/40_custom config file&#8230; taking a peek at the /boot/grub/grub.cfg generated on the new ubuntu 19.10 system&#8230; ran grub-install /dev/sda & grub-install /dev/sdb&#8230; followed by an update-grub in order to recreate my clean custom menu&#8230; 

I proceeded to reboot from this menu&#8230; and sure enough&#8230; I ran pretty much into the same problem: the boot process stalls and I get what looks like the same kernel crash with the same backtrace. Seems the kernel is not quite dead since it loops into the same sequence at something like a 1-2 minutes interval.

I've looked around a bit and there seem to be a few tickets open with somewhat similar issues involving grub 2.02 and newer kernels - either from fresh installs or an upgrade to ubuntu 19.10. 

Couldn't make much sense of them as they appear to be more UEFI/secure-boot centered (?) - my system runs an old BIOS based non-UEFI/TPM at bootup&#8230;

Not sure what I should do at this point&#8230; open an issue with debian support&#8230; or perhaps on the help-grub mailing list? Or perhaps wait and hope someone backports the newer grub to debian/stable (buster)?

In any case this suggests that should I decide to wait for ubuntu 20.04 the chances are that I will run into the same problem.

---

### Post by ubfan1 on 2019-10-21
Random... hmmmmm....  See [https://lwn.net/Articles/802360/](https://lwn.net/Articles/802360/)  Suggests trying an earlier kernel, although I haven't read the full story.  18.04.1 should come with the 4.15 kernel.  20.04 may get the 5.4 (or later)  kernel with the fix.

---

### Post by chris_jones2 on 2019-10-22
Well since my #2 install booted fine from the grub menu it had generated I thought&#8230; maybe grub 2.0 is not the culprit but rather the 2.0 style entry that I had duplicated from the 18.04 stanza in my /etc/grub.d/40_custom config file.

So I did a mount /dev/sdb7 and took a quick look at the new ubuntu system's /boot/grub/grub.cfg and saw that the entry generated by the new ubuntu install &#8212; apart from some conditionals that looked xen- oriented? &#8230; so I just ignored those &#8212; had the following extra three lines right at the top of the stanza:

> recordfail
> load_video
> gfxmode $linux_gfx_mode
 
Why not give it a shot&#8230; ? So I added the above three lines and rebooted .. and though grub 2.02 did complain a bit about the recordfail command &#8212; probably a new feature in grub 2.04 (?) &#8230; I was able to boot successfully into the new 19.10 install&#8230;

The $linux_gfx_mode likely contains what I specified in /etc/defaults/grub:

GRUB_GFXMODE=1920x1200

As to what load_video does&#8230; I have no idea&#8230; but as I 'understand' :-) it&#8230; in order to boot recent kernels successfully&#8230; grub needs to be explicitly told that you will not be satisfied with the good old VGA-style (640x480?) pure text mode linux console&#8230;

From the few issues I have found&#8230; this seems to have been necessary with all kernels in a UEFI context for some time&#8230; and for reasons unknown&#8230; with newer kernels this has become necessary even if you're booting an old BIOS based machine.?

Anyway since I'm sure just about everybody is happy with the grub menus gen'd automatically by grub+OS-prober&#8230; which should take care of generating valid grub menu entries under all circumstances&#8230; and this has turned out to have been yet another user error on my part&#8230; I see little point investigating further.    

Thanks to those who have responded.

CJ

---

