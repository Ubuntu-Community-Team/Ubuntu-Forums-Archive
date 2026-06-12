---
title: "Touchpad isn't working in Mint [Acer V15 Nitro Black Edition]"
date: 2015-04-29
forum: MINT
---

### Post by Lucas_Germano on 2015-04-29
Hello guys,

I have a dual boot Windows 8.1 and Mint 17.1 and my touchpad doesn’t work in Mint, and it didn't when i had to use Boot Repair aswell.

My xinput list command outputs this:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SteelSeries Sensei Raw Gaming Mouse         id=15    [slave  pointer  (2)]
&#9116;   &#8627; SteelSeries Sensei Raw Gaming Mouse         id=17    [slave  pointer  (2)]
&#9116;   &#8627;                                             id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; SteelSeries Sensei Raw Gaming Mouse         id=16    [slave  keyboard (3)]
```

I tried 
```
sudo modprobe -r psmouse
   sudo modprobe psmouse
```
and it didn't work aswell, anyone have any ideia what coudl it be?


Any help would be appreciated.

---

