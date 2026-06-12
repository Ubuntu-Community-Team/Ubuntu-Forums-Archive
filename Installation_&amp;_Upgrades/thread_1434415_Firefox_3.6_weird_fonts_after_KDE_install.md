---
title: "Firefox 3.6 weird fonts after KDE install"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by tommazzo on 2010-03-20
Hello everyone,

I am new to Linux and I am using Ubuntu 9.10 x64.

I am having the weird fonts problem (fonts look kind of reddish) in  Firefox 3.6 that has been discussed quite a lot on the web already. I  modified the contents of my ~/fonts.conf file according to the proposed  fix and that solved the problem until I installed KDE 4.4  (kubuntu-desktop) today. Now the fonts in Firefox look weird again in  both KDE and Gnome, even though I set KDE to use antialiasing with  slight hinting and made sure that the .fonts.conf file has still the  proper contents. What can I do to fix this problem?

Here the contents of my .fonts.conf file:
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
        <match target="font" >
               <edit mode="assign" name="rgba" >
                       <const>none</const>
               </edit>
    </match>
    <match target="font" >
               <edit mode="assign" name="hinting" >
                      <bool>true</bool>
               </edit>
        </match>
        <match target="font" >
               <edit mode="assign" name="hintstyle" >
                      <const>hintslight</const> 
       </edit>
        </match>
        <match target="font" >
               <edit mode="assign" name="antialias" >
                       <bool>true</bool>  
       </edit>
    </match>
</fontconfig>

---

