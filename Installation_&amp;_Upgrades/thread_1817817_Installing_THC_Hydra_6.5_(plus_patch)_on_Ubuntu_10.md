---
title: "Installing THC Hydra 6.5 (plus patch) on Ubuntu 10.10 Maverick Meerkat"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by atomicben on 2011-08-03
This is a how to for installing THC-Hydra 6.5 (AND apply the diff patch) on Ubuntu 10.10 (Maverick Meerkat) with SSL support.  This will also install the HydraGTK (the GUI front for hydra).

*****NOTE: There is no reason (that I know of) that this won't work versions higher that 10.10.  ***

These instructions are a combination of:

[http://ubuntuforums.org/showthread.php?t=1800683](http://ubuntuforums.org/showthread.php?t=1800683) by etherspin
[http://edwincastillo.com/archives/242](http://edwincastillo.com/archives/242) by Edwin Castillo
and my own experiences

Although both of those sources are good I had to use bits of each tut to get the latest THC HYDRA working on 10.10

My intention is to provide clear and easy steps without having to figure out how to tweak and play like I did.

*****NOTE: Do NOT type the stuff you see in the OUTPUT or QUOTE boxes, I have provided the outputs so you know you're on the right track.  You know, like when you pass a landmark while following directions that let's you know you haven't f*ed up.***


[B]Step 1: Open a terminal
[/B] 
you know how to do this right?

**Step 2: Installing everything you need to compile THC HYDRA from source**

```
sudo apt-get install build-essential linux-headers-$(uname -r) libgtk2.0-dev libssl-dev cmake patch
```**Step 3: Download the THC HYDRA source code**

```
wget -c http://thc.org/thc-hydra/releases/hydra-6.5-src.tar.gz
```**Step 4: Extract the source code**

```
tar -xvzf hydra-6.5-src.tar.gz
cd hydra-6.5-src
```**Step 5: download the diff (this is a patch to version 6.5)**
```

wget -c http://thc.org/thc-hydra/hydra-6.5-fix.diff
```**Step 6: Apply the patch**

```
patch < hydra-6.5-fix.diff
```Output:
> patching file hydra-http-form.c
patching file hydra.c**Step 7: Configure**
```

./configure
```Output:
> 
Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...
now type "make"
**Step 8: Make (compile)** BE PATIENT

```
make
```Output:
> 
If men could get pregnant, abortion would be a sacrament

cd hydra-gtk && sh ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
`src/xhydra' -> `../xhydra'
The GTK GUI is ready, type "./xhydra" to start[B]
Step 9: Install (make install)[/B]

```
sudo make install
```Output:
> strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
echo OK > /dev/null && test -x xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra || echo OK > /dev/null
mkdir -p /usr/local/man/man1
cp -f hydra.1 xhydra.1 pw-inspector.1 /usr/local/man/man1Step 10:

[B]You are finished!  You can now use hydra from the command line.  For help type:
hydra[/B]


If you want to use the GUI (graphical user interface) aka. the GTK you have a couple choices.

1. just type 
**xhydra **
and hit enter 
the thing that sucks about this method is that the terminal window stays open while you use it.

2. press **ALT+F2** then type 
**xhydra **
this is much nicer but of course you have to do the whole ALT+F2 thing

3. make yourself a menu shortcut that calls **xhydra**

Done!

---

