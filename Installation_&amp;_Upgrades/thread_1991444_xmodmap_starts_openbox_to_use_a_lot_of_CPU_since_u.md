---
title: "xmodmap starts openbox to use a lot of CPU since upgrade to Ubuntu 12.04"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2012-05-30
Hello everybody

This question is not very urgent, but embarassing for me.

I have my own keyboard-layout and therefore my own ".Xmodmap" file.
(see [www.freimann.eu/eliphi/phi/keyboard]("http://www.freimann.eu/eliphi/phi/keyboard"))

Since the upgrade to Ubuntu 12.04 (I use the Server Edition together with LXDE) **openbox** **uses a lot of CPU-time** whenever I switch to my keyboard layout

```
xmodmap ~/.Xmodmap
```

(I don't use this often, because after login to LXDE it starts automatically, but after suspend it has to be done manually.)

It could be a problem in my .Xmodmap file? Any help on that is very kind.

~/.Xmodmap:
```
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
! kiffi board (phi) : Sort of Neo or Dvorak for german programmers !!
!                     This is a transitional layout, which only swaps the most
!                     used letters to the ones on the initial finger position.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
! First impl: Layout: Lenovo X61 Tablet-Thinkpad - Ubuntu 8.10
!             phi: 7. 1. 2009
!
! Version 2.0 Mai 2012: Layout for wasdkeyboards.com (inkl. "geek-hack")


!!!!!!!!!!!!!!!!!!!!! Modifiers !!!!!!!!!!!!!!!!!!!!!!!!!
clear Shift
clear Lock
clear Control
clear mod1
clear mod2
clear mod3
clear mod4
clear mod5

!!!!!!!!!!!!!!!!!! Modifier Keys !!!!!!!!!!!!!!!!!!!!!!!!!!!!

! left & right alt and ctrl are treated same:
!Both control keys as symbol "Control" (and Capslock also: 66)
keycode  66 = Control_L
keycode 105 = Control_R
keycode  37 = Control_L

!both alt keys as symbol (mod1)
keycode  64  = Alt_L
keycode 108  = Alt_R

!Right "windows (geek/hack) key is meta (as ESC) used for Emacs (mod2)
!keycode 117 = Hyper_R
!keycode 227 = Meta_R
keycode 134 = Super_R

!menu-key
keycode 135 = Menu

!"Pause" is treated as Multi_Key (mod 3)
keycode 127 = Multi_key

!Num Lock key as Num_Lock (mod 4)
keycode 77 = Num_Lock
!keycode 77 =

!Windows keys as Mode_switch (mod 5)
keycode 133 = Mode_switch


keycode 119  = Delete

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!                    K E Y S (Glyphs)                 !
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!for all keycodes:
!keycode   A = A; Shift-A, Mode_Switch-A; Mode_Switch-Shift-A 

! arrows
keycode 113  = Left
keycode 114  = Right
keycode 111  = Up
keycode 116  = Down


keycode 10   = 1 0x0021 onesuperior 0x00A1
!              1 !      ¹           ¡
keycode 11   = 2 at twosuperior copyright
keycode 12   = 3 0x0023 threesuperior
keycode 13   = 4 dollar EuroSign 0x00A3
!              4 $      €        £
keycode 14   = 5 percent
keycode 15   = 6 0x005E
keycode 16   = 7 ampersand
keycode 17   = 8 asterisk
keycode 18   = 9 parenleft
keycode 19   = 0 parenright
keycode 20   = minus underscore ssharp ssharp
keycode 21   = equal plus 0x00AC


!backspace
keycode  22  = BackSpace BackSpace 0xFD1A

!tabulator
keycode 23   = Tab

keycode 24   = q Q
keycode 25   = w W 
keycode 26   = l L
keycode 27   = v V
keycode 28   = j J
keycode 29   = z Z
keycode 30   = u U uacute ugrave
keycode 31   = k K
keycode 32   = h H
keycode 33   = p P U03C6 U03A6
keycode 34   = braceleft braceright udiaeresis Udiaeresis
keycode 35   = bracketleft bracketright 

keycode 38   = t T
keycode 39   = s S
keycode 40   = r R 0x00AE
keycode 41   = n N ntilde Ntilde
keycode 42   = g G
keycode 43   = o O oacute ograve
keycode 44   = e E eacute egrave
keycode 45   = i I iacute igrave
keycode 46   = a A aacute agrave

keycode 47   = semicolon colon odiaeresis Odiaeresis
keycode 48   = apostrophe quotedbl adiaeresis Adiaeresis
keycode 49   = 0x0060  0x007E 

keycode 51   = backslash 0x007C 

keycode 52   = y Y
keycode 53   = b B
keycode 54   = c C ccedilla Ccedilla
keycode 55   = d D
keycode 56   = x X
keycode 57   = f F
keycode 58   = m M

keycode 59   = comma  0x003C
!                     <      
keycode 60   = period 0x003E
!                     >      
keycode 61   = slash  0x003F 0x00BF
!              /      ?      ¿

! Numeric KeyPad
keycode 87   = 1
keycode 88   = 2
keycode 89   = 3
keycode 83   = 4
keycode 84   = 5
keycode 85   = 6
keycode 79   = 7
keycode 80   = 8
keycode 81   = 9
keycode 90   = 0
keycode 91   = period
 
keycode 106  = KP_Divide
keycode 63   = KP_Multiply
keycode 82   = KP_Subtract
keycode 86   = KP_Add
keycode 104  = KP_Enter


!!!!!!!!!!! Set up Modifiers (Meta keys) !!!!!!!!!!!!!!!!!!
add Shift   = Shift_L Shift_R
add Lock    = Caps_Lock
add Control = Control_R Control_L
add mod1    = Alt_L Alt_R
add mod2    = Super_R
add mod3    = Multi_key
add mod4    = Num_Lock
add mod5    = Mode_switch
```

---

