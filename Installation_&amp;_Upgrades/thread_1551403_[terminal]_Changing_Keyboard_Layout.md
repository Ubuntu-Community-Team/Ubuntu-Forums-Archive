---
title: "[terminal] Changing Keyboard Layout?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-08-12
Hello

I'm trying to use the Xubuntu-based BitDefender Rescue Disk, and having an issue. Posting in their forum didn't return anything, so I figured I should ask here next.

I can successfully boot up BitDefender in French on a laptop from a USB key, but when I launch Terminal, the layout is for the US keyboard, and "loadkeys fr" just outputs an error (""Unknown keysim 'trademark'").

Does someone know how to change the keyboard layout in the command-line?

Thank you.

---

### Post by MorleyPotter on 2010-08-12
> **littlebigman said:**
> Hello

I'm trying to use the Xubuntu-based BitDefender Rescue Disk, and having an issue. Posting in their forum didn't return anything, so I figured I should ask here next.

I can successfully boot up BitDefender in French on a laptop from a USB key, but when I launch Terminal, the layout is for the US keyboard, and "loadkeys fr" just outputs an error (""Unknown keysim 'trademark'").

Does someone know how to change the keyboard layout in the command-line?

Thank you.


I think you use
[I][I]setxkbmap

try man [/I][/I]*[I]setxkbmap for details.*[/I]

---

### Post by littlebigman on 2010-08-12
Thanks, but no go :-/

Tried this:
1. apt-get install console-data: Chose AZERTY/France
2. setxkbmap
3. setxkbmap -layout fr 
4. setxkbmap -display 127.0.0.1:0.0 -layout fr

All result in "Cannot open display". I guess it's X-related but I'm no expert of this thing.

Anybody knows what I could try?

Thank you.

---

### Post by simosx on 2010-08-12
Do you mean the 'Linux console' (like what some old people call the "DOS prompt")? 

In that case, then it's indeed 'loadkeys' that you use to configure a layout.
The 'setxkbmap' is for the graphical interface so they do not apply here.

AFAIK, the use of 'loadkeys' and the Linux console does not take much attention. In Ubuntu you even need to install the package for the Linux console layouts. 

Do the proper thing, run 'loadkeys' with the --verbose flag and check to find the source of the problem.

---

### Post by littlebigman on 2010-08-12
Thanks for the help. Here's the output of "loadkeys --verbose fr" typed in a terminal window in X:

```

Loading /usr/share/keymaps/i386/azerty/fr.kmap.gz
switching to azerty-layout
switching to linux-with-alt-and-altgr
switching to linux-keys-bare
keycode 1, table 0 = 27
keycode 2, table 0 = 38
keycode 3, table 0 = 123
keycode 4, table 0 = 34
keycode 5, table 0 = 39
keycode 6, table 0 = 40
keycode 7, table 0 = 45
keycode 8, table 0 = 125
keycode 9, table 0 = 95
keycode 10, table 0 = 47
keycode 11, table 0 = 64
keycode 12, table 0 = 41
keycode 13, table 0 = 61
keycode 14, table 0 = 127
keycode 15, table 0 = 9
keycode 16, table 0 = 2913
keycode 17, table 0 = 2938
keycode 18, table 0 = 2917
keycode 19, table 0 = 2930
keycode 20, table 0 = 2932
keycode 21, table 0 = 2937
keycode 22, table 0 = 2933
keycode 23, table 0 = 2921
keycode 24, table 0 = 2927
keycode 25, table 0 = 2928
keycode 26, table 0 = 94
keycode 27, table 0 = 36
keycode 28, table 0 = 513
keycode 29, table 0 = 1794
keycode 30, table 0 = 2929
keycode 31, table 0 = 2931
keycode 32, table 0 = 2916
keycode 33, table 0 = 2918
keycode 34, table 0 = 2919
keycode 35, table 0 = 2920
keycode 36, table 0 = 2922
keycode 37, table 0 = 2923
keycode 38, table 0 = 2924
keycode 39, table 0 = 2925
keycode 40, table 0 = 124
keycode 41, table 0 = 42
keycode 42, table 0 = 1792
keycode 43, table 0 = 42
keycode 44, table 0 = 2935
keycode 45, table 0 = 2936
keycode 46, table 0 = 2915
keycode 47, table 0 = 2934
keycode 48, table 0 = 2914
keycode 49, table 0 = 2926
keycode 50, table 0 = 44
keycode 51, table 0 = 59
keycode 52, table 0 = 58
keycode 53, table 0 = 33
keycode 54, table 0 = 1792
keycode 55, table 0 = 780
keycode 56, table 0 = 1795
keycode 57, table 0 = 32
keycode 58, table 0 = 519
keycode 59, table 0 = 256
keycode 60, table 0 = 257
keycode 61, table 0 = 258
keycode 62, table 0 = 259
keycode 63, table 0 = 260
keycode 64, table 0 = 261
keycode 65, table 0 = 262
keycode 66, table 0 = 263
keycode 67, table 0 = 264
keycode 68, table 0 = 265
keycode 69, table 0 = 520
keycode 70, table 0 = 521
keycode 71, table 0 = 775
keycode 72, table 0 = 776
keycode 73, table 0 = 777
keycode 74, table 0 = 779
keycode 75, table 0 = 772
keycode 76, table 0 = 773
keycode 77, table 0 = 774
keycode 78, table 0 = 778
keycode 79, table 0 = 769
keycode 80, table 0 = 770
keycode 81, table 0 = 771
keycode 82, table 0 = 768
keycode 83, table 0 = 784
keycode 84, table 0 = 518
keycode 86, table 0 = 60
keycode 87, table 0 = 266
keycode 88, table 0 = 267
keycode 96, table 0 = 782
keycode 97, table 0 = 1794
keycode 98, table 0 = 781
keycode 99, table 0 = 512
keycode 100, table 0 = 1793
keycode 101, table 0 = 517
keycode 102, table 0 = 276
keycode 103, table 0 = 1539
keycode 104, table 0 = 280
keycode 105, table 0 = 1537
keycode 106, table 0 = 1538
keycode 107, table 0 = 279
keycode 108, table 0 = 1536
keycode 109, table 0 = 281
keycode 110, table 0 = 277
keycode 111, table 0 = 278
keycode 119, table 0 = 285
keycode 1, table 1 = 27
keycode 2, table 1 = 49
keycode 3, table 1 = 50
keycode 4, table 1 = 51
keycode 5, table 1 = 52
keycode 6, table 1 = 53
keycode 7, table 1 = 54
keycode 8, table 1 = 55
keycode 9, table 1 = 56
keycode 10, table 1 = 57
keycode 11, table 1 = 48
keycode 12, table 1 = 93
keycode 13, table 1 = 43
keycode 14, table 1 = 127
keycode 15, table 1 = 9
keycode 16, table 1 = 2881
keycode 17, table 1 = 2906
keycode 18, table 1 = 2885
keycode 19, table 1 = 2898
keycode 20, table 1 = 2900
keycode 21, table 1 = 2905
keycode 22, table 1 = 2901
keycode 23, table 1 = 2889
keycode 24, table 1 = 2895
keycode 25, table 1 = 2896
keycode 26, table 1 = 60
keycode 27, table 1 = 62
keycode 28, table 1 = 513
keycode 29, table 1 = 1794
keycode 30, table 1 = 2897
keycode 31, table 1 = 2899
keycode 32, table 1 = 2884
keycode 33, table 1 = 2886
keycode 34, table 1 = 2887
keycode 35, table 1 = 2888
keycode 36, table 1 = 2890
keycode 37, table 1 = 2891
keycode 38, table 1 = 2892
keycode 39, table 1 = 2893
keycode 40, table 1 = 37
keycode 41, table 1 = 126
keycode 42, table 1 = 1792
keycode 43, table 1 = 35
keycode 44, table 1 = 2903
keycode 45, table 1 = 2904
keycode 46, table 1 = 2883
keycode 47, table 1 = 2902
keycode 48, table 1 = 2882
keycode 49, table 1 = 2894
keycode 50, table 1 = 63
keycode 51, table 1 = 46
keycode 52, table 1 = 47
keycode 53, table 1 = 92
keycode 54, table 1 = 1792
keycode 55, table 1 = 780
keycode 56, table 1 = 1795
keycode 57, table 1 = 32
keycode 58, table 1 = 519
keycode 59, table 1 = 268
keycode 60, table 1 = 269
keycode 61, table 1 = 270
keycode 62, table 1 = 271
keycode 63, table 1 = 272
keycode 64, table 1 = 273
keycode 65, table 1 = 274
keycode 66, table 1 = 275
keycode 67, table 1 = 286
keycode 68, table 1 = 287
keycode 69, table 1 = 520
keycode 70, table 1 = 515
keycode 71, table 1 = 775
keycode 72, table 1 = 776
keycode 73, table 1 = 777
keycode 74, table 1 = 779
keycode 75, table 1 = 772
keycode 76, table 1 = 773
keycode 77, table 1 = 774
keycode 78, table 1 = 778
keycode 79, table 1 = 769
keycode 80, table 1 = 770
keycode 81, table 1 = 771
keycode 82, table 1 = 768
keycode 83, table 1 = 784
keycode 84, table 1 = 518
keycode 86, table 1 = 62
keycode 87, table 1 = 288
keycode 88, table 1 = 289
keycode 96, table 1 = 782
keycode 97, table 1 = 1794
keycode 98, table 1 = 781
keycode 99, table 1 = 512
keycode 100, table 1 = 1793
keycode 101, table 1 = 517
keycode 102, table 1 = 276
keycode 103, table 1 = 1539
keycode 104, table 1 = 523
keycode 105, table 1 = 1537
keycode 106, table 1 = 1538
keycode 107, table 1 = 279
keycode 108, table 1 = 1536
keycode 109, table 1 = 522
keycode 110, table 1 = 277
keycode 111, table 1 = 278
keycode 119, table 1 = 285
keycode 1, table 2 = 512
keycode 2, table 2 = 512
keycode 3, table 2 = 126
keycode 4, table 2 = 35
keycode 5, table 2 = 123
keycode 6, table 2 = 91
keycode 7, table 2 = 124
keycode 8, table 2 = 96
keycode 9, table 2 = 92
keycode 10, table 2 = 94
keycode 11, table 2 = 64
keycode 12, table 2 = 93
keycode 13, table 2 = 125
keycode 14, table 2 = 512
keycode 15, table 2 = 512
keycode 16, table 2 = 2913
keycode 17, table 2 = 2938
keycode 18, table 2 = 2917
keycode 19, table 2 = 2930
keycode 20, table 2 = 2932
keycode 21, table 2 = 2937
keycode 22, table 2 = 2933
keycode 23, table 2 = 2921
keycode 24, table 2 = 2927
keycode 25, table 2 = 2928
keycode 26, table 2 = 512
keycode 27, table 2 = 126
keycode 28, table 2 = 513
keycode 29, table 2 = 1794
keycode 30, table 2 = 2929
keycode 31, table 2 = 2931
keycode 32, table 2 = 2916
keycode 33, table 2 = 2918
keycode 34, table 2 = 2919
keycode 35, table 2 = 2920
keycode 36, table 2 = 2922
keycode 37, table 2 = 2923
keycode 38, table 2 = 2924
keycode 39, table 2 = 2925
keycode 40, table 2 = 512
keycode 41, table 2 = 512
keycode 42, table 2 = 1792
keycode 43, table 2 = 512
keycode 44, table 2 = 2935
keycode 45, table 2 = 2936
keycode 46, table 2 = 2915
keycode 47, table 2 = 2934
keycode 48, table 2 = 2914
keycode 49, table 2 = 2926
keycode 50, table 2 = 512
keycode 51, table 2 = 512
keycode 52, table 2 = 512
keycode 53, table 2 = 512
keycode 54, table 2 = 1792
keycode 55, table 2 = 2326
keycode 56, table 2 = 1795
keycode 57, table 2 = 512
keycode 58, table 2 = 519
keycode 69, table 2 = 2324
keycode 70, table 2 = 514
keycode 71, table 2 = 2321
keycode 72, table 2 = 2322
keycode 73, table 2 = 2323
keycode 74, table 2 = 2327
keycode 75, table 2 = 2318
keycode 76, table 2 = 2319
keycode 77, table 2 = 2320
keycode 78, table 2 = 2328
keycode 79, table 2 = 2315
keycode 80, table 2 = 2316
keycode 81, table 2 = 2317
keycode 82, table 2 = 2314
keycode 83, table 2 = 784
keycode 84, table 2 = 518
keycode 86, table 2 = 124
keycode 96, table 2 = 2329
keycode 97, table 2 = 1794
keycode 98, table 2 = 2325
keycode 99, table 2 = 512
keycode 100, table 2 = 1793
keycode 101, table 2 = 517
keycode 102, table 2 = 276
keycode 103, table 2 = 1539
keycode 104, table 2 = 280
keycode 105, table 2 = 1537
keycode 106, table 2 = 1538
keycode 107, table 2 = 279
keycode 108, table 2 = 1536
keycode 109, table 2 = 281
keycode 110, table 2 = 277
keycode 111, table 2 = 278
keycode 119, table 2 = 285
keycode 1, table 4 = 512
keycode 2, table 4 = 512
keycode 3, table 4 = 0
keycode 4, table 4 = 27
keycode 5, table 4 = 28
keycode 6, table 4 = 29
keycode 7, table 4 = 30
keycode 8, table 4 = 31
keycode 9, table 4 = 127
keycode 10, table 4 = 512
keycode 11, table 4 = 512
keycode 12, table 4 = 31
keycode 13, table 4 = 512
keycode 14, table 4 = 512
keycode 15, table 4 = 512
keycode 16, table 4 = 1
keycode 17, table 4 = 26
keycode 18, table 4 = 5
keycode 19, table 4 = 18
keycode 20, table 4 = 20
keycode 21, table 4 = 25
keycode 22, table 4 = 21
keycode 23, table 4 = 9
keycode 24, table 4 = 15
keycode 25, table 4 = 16
keycode 26, table 4 = 27
keycode 27, table 4 = 29
keycode 28, table 4 = 513
keycode 29, table 4 = 1794
keycode 30, table 4 = 17
keycode 31, table 4 = 19
keycode 32, table 4 = 4
keycode 33, table 4 = 6
keycode 34, table 4 = 7
keycode 35, table 4 = 8
keycode 36, table 4 = 10
keycode 37, table 4 = 11
keycode 38, table 4 = 12
keycode 39, table 4 = 13
keycode 40, table 4 = 7
keycode 41, table 4 = 0
keycode 42, table 4 = 1792
keycode 43, table 4 = 28
keycode 44, table 4 = 23
keycode 45, table 4 = 24
keycode 46, table 4 = 3
keycode 47, table 4 = 22
keycode 48, table 4 = 2
keycode 49, table 4 = 14
keycode 50, table 4 = 512
keycode 51, table 4 = 512
keycode 52, table 4 = 512
keycode 53, table 4 = 127
keycode 54, table 4 = 1792
keycode 55, table 4 = 780
keycode 56, table 4 = 1795
keycode 57, table 4 = 0
keycode 58, table 4 = 519
keycode 59, table 4 = 290
keycode 60, table 4 = 291
keycode 61, table 4 = 292
keycode 62, table 4 = 293
keycode 63, table 4 = 294
keycode 64, table 4 = 295
keycode 65, table 4 = 296
keycode 66, table 4 = 297
keycode 67, table 4 = 298
keycode 68, table 4 = 299
keycode 69, table 4 = 520
keycode 70, table 4 = 516
keycode 71, table 4 = 775
keycode 72, table 4 = 776
keycode 73, table 4 = 777
keycode 74, table 4 = 779
keycode 75, table 4 = 772
keycode 76, table 4 = 773
keycode 77, table 4 = 774
keycode 78, table 4 = 778
keycode 79, table 4 = 769
keycode 80, table 4 = 770
keycode 81, table 4 = 771
keycode 82, table 4 = 768
keycode 83, table 4 = 784
keycode 84, table 4 = 518
keycode 86, table 4 = 512
keycode 87, table 4 = 300
keycode 88, table 4 = 301
keycode 96, table 4 = 782
keycode 97, table 4 = 1794
keycode 98, table 4 = 781
keycode 99, table 4 = 28
keycode 100, table 4 = 1793
keycode 101, table 4 = 517
keycode 102, table 4 = 276
keycode 103, table 4 = 1539
keycode 104, table 4 = 280
keycode 105, table 4 = 1537
keycode 106, table 4 = 1538
keycode 107, table 4 = 279
keycode 108, table 4 = 1536
keycode 109, table 4 = 281
keycode 110, table 4 = 277
keycode 111, table 4 = 278
keycode 119, table 4 = 285
keycode 1, table 6 = 512
keycode 2, table 6 = 512
keycode 3, table 6 = 512
keycode 4, table 6 = 512
keycode 5, table 6 = 512
keycode 6, table 6 = 512
keycode 7, table 6 = 512
keycode 8, table 6 = 512
keycode 9, table 6 = 512
keycode 10, table 6 = 512
keycode 11, table 6 = 512
keycode 12, table 6 = 512
keycode 13, table 6 = 512
keycode 14, table 6 = 512
keycode 15, table 6 = 512
keycode 16, table 6 = 1
keycode 17, table 6 = 26
keycode 18, table 6 = 5
keycode 19, table 6 = 18
keycode 20, table 6 = 20
keycode 21, table 6 = 25
keycode 22, table 6 = 21
keycode 23, table 6 = 9
keycode 24, table 6 = 15
keycode 25, table 6 = 16
keycode 26, table 6 = 512
keycode 27, table 6 = 512
keycode 28, table 6 = 513
keycode 29, table 6 = 1794
keycode 30, table 6 = 17
keycode 31, table 6 = 19
keycode 32, table 6 = 4
keycode 33, table 6 = 6
keycode 34, table 6 = 7
keycode 35, table 6 = 8
keycode 36, table 6 = 10
keycode 37, table 6 = 11
keycode 38, table 6 = 12
keycode 39, table 6 = 13
keycode 40, table 6 = 512
keycode 41, table 6 = 512
keycode 42, table 6 = 1792
keycode 43, table 6 = 512
keycode 44, table 6 = 23
keycode 45, table 6 = 24
keycode 46, table 6 = 3
keycode 47, table 6 = 22
keycode 48, table 6 = 2
keycode 49, table 6 = 14
keycode 50, table 6 = 512
keycode 51, table 6 = 512
keycode 52, table 6 = 512
keycode 53, table 6 = 512
keycode 54, table 6 = 1792
keycode 55, table 6 = 780
keycode 56, table 6 = 1795
keycode 57, table 6 = 512
keycode 58, table 6 = 519
keycode 69, table 6 = 520
keycode 71, table 6 = 775
keycode 72, table 6 = 776
keycode 73, table 6 = 777
keycode 74, table 6 = 779
keycode 75, table 6 = 772
keycode 76, table 6 = 773
keycode 77, table 6 = 774
keycode 78, table 6 = 778
keycode 79, table 6 = 769
keycode 80, table 6 = 770
keycode 81, table 6 = 771
keycode 82, table 6 = 768
keycode 83, table 6 = 524
keycode 84, table 6 = 518
keycode 86, table 6 = 512
keycode 96, table 6 = 782
keycode 97, table 6 = 1794
keycode 98, table 6 = 781
keycode 99, table 6 = 512
keycode 100, table 6 = 1793
keycode 101, table 6 = 517
keycode 102, table 6 = 276
keycode 103, table 6 = 1539
keycode 104, table 6 = 280
keycode 105, table 6 = 1537
keycode 106, table 6 = 1538
keycode 107, table 6 = 279
keycode 108, table 6 = 1536
keycode 109, table 6 = 281
keycode 110, table 6 = 277
keycode 111, table 6 = 524
keycode 119, table 6 = 285
keycode 1, table 8 = 2075
keycode 2, table 8 = 2097
keycode 3, table 8 = 2098
keycode 4, table 8 = 2099
keycode 5, table 8 = 2100
keycode 6, table 8 = 2101
keycode 7, table 8 = 2102
keycode 8, table 8 = 2103
keycode 9, table 8 = 2104
keycode 10, table 8 = 2105
keycode 11, table 8 = 2096
keycode 12, table 8 = 2093
keycode 13, table 8 = 2109
keycode 14, table 8 = 2175
keycode 15, table 8 = 2057
keycode 16, table 8 = 2145
keycode 17, table 8 = 2170
keycode 18, table 8 = 2149
keycode 19, table 8 = 2162
keycode 20, table 8 = 2164
keycode 21, table 8 = 2169
keycode 22, table 8 = 2165
keycode 23, table 8 = 2153
keycode 24, table 8 = 2159
keycode 25, table 8 = 2160
keycode 26, table 8 = 2139
keycode 27, table 8 = 2141
keycode 28, table 8 = 2061
keycode 29, table 8 = 1794
keycode 30, table 8 = 2161
keycode 31, table 8 = 2163
keycode 32, table 8 = 2148
keycode 33, table 8 = 2150
keycode 34, table 8 = 2151
keycode 35, table 8 = 2152
keycode 36, table 8 = 2154
keycode 37, table 8 = 2155
keycode 38, table 8 = 2156
keycode 39, table 8 = 2157
keycode 40, table 8 = 2087
keycode 41, table 8 = 2144
keycode 42, table 8 = 1792
keycode 43, table 8 = 2140
keycode 44, table 8 = 2167
keycode 45, table 8 = 2168
keycode 46, table 8 = 2147
keycode 47, table 8 = 2166
keycode 48, table 8 = 2146
keycode 49, table 8 = 2158
keycode 50, table 8 = 512
keycode 51, table 8 = 2092
keycode 52, table 8 = 2094
keycode 53, table 8 = 2095
keycode 54, table 8 = 1792
keycode 55, table 8 = 780
keycode 56, table 8 = 1795
keycode 57, table 8 = 2080
keycode 58, table 8 = 519
keycode 59, table 8 = 1280
keycode 60, table 8 = 1281
keycode 61, table 8 = 1282
keycode 62, table 8 = 1283
keycode 63, table 8 = 1284
keycode 64, table 8 = 1285
keycode 65, table 8 = 1286
keycode 66, table 8 = 1287
keycode 67, table 8 = 1288
keycode 68, table 8 = 1289
keycode 69, table 8 = 520
keycode 70, table 8 = 521
keycode 71, table 8 = 2311
keycode 72, table 8 = 2312
keycode 73, table 8 = 2313
keycode 74, table 8 = 779
keycode 75, table 8 = 2308
keycode 76, table 8 = 2309
keycode 77, table 8 = 2310
keycode 78, table 8 = 778
keycode 79, table 8 = 2305
keycode 80, table 8 = 2306
keycode 81, table 8 = 2307
keycode 82, table 8 = 2304
keycode 83, table 8 = 784
keycode 84, table 8 = 518
keycode 86, table 8 = 2108
keycode 87, table 8 = 1290
keycode 88, table 8 = 1291
keycode 96, table 8 = 782
keycode 97, table 8 = 1794
keycode 98, table 8 = 781
keycode 99, table 8 = 28
keycode 100, table 8 = 1793
keycode 101, table 8 = 517
keycode 102, table 8 = 276
keycode 103, table 8 = 530
keycode 104, table 8 = 280
keycode 105, table 8 = 528
keycode 106, table 8 = 529
keycode 107, table 8 = 279
keycode 108, table 8 = 1536
keycode 109, table 8 = 281
keycode 110, table 8 = 277
keycode 111, table 8 = 278
keycode 119, table 8 = 285
keycode 1, table 12 = 512
keycode 2, table 12 = 512
keycode 3, table 12 = 512
keycode 4, table 12 = 512
keycode 5, table 12 = 512
keycode 6, table 12 = 512
keycode 7, table 12 = 512
keycode 8, table 12 = 512
keycode 9, table 12 = 512
keycode 10, table 12 = 512
keycode 11, table 12 = 512
keycode 12, table 12 = 512
keycode 13, table 12 = 512
keycode 14, table 12 = 512
keycode 15, table 12 = 512
keycode 16, table 12 = 2049
keycode 17, table 12 = 2074
keycode 18, table 12 = 2053
keycode 19, table 12 = 2066
keycode 20, table 12 = 2068
keycode 21, table 12 = 2073
keycode 22, table 12 = 2069
keycode 23, table 12 = 2057
keycode 24, table 12 = 2063
keycode 25, table 12 = 2064
keycode 26, table 12 = 512
keycode 27, table 12 = 512
keycode 28, table 12 = 513
keycode 29, table 12 = 1794
keycode 30, table 12 = 2065
keycode 31, table 12 = 2067
keycode 32, table 12 = 2052
keycode 33, table 12 = 2054
keycode 34, table 12 = 2055
keycode 35, table 12 = 2056
keycode 36, table 12 = 2058
keycode 37, table 12 = 2059
keycode 38, table 12 = 2060
keycode 39, table 12 = 2061
keycode 40, table 12 = 512
keycode 41, table 12 = 512
keycode 42, table 12 = 1792
keycode 43, table 12 = 512
keycode 44, table 12 = 2071
keycode 45, table 12 = 2072
keycode 46, table 12 = 2051
keycode 47, table 12 = 2070
keycode 48, table 12 = 2050
keycode 49, table 12 = 2062
keycode 50, table 12 = 512
keycode 51, table 12 = 512
keycode 52, table 12 = 512
keycode 53, table 12 = 512
keycode 54, table 12 = 1792
keycode 55, table 12 = 780
keycode 56, table 12 = 1795
keycode 57, table 12 = 512
keycode 58, table 12 = 519
keycode 59, table 12 = 1280
keycode 60, table 12 = 1281
keycode 61, table 12 = 1282
keycode 62, table 12 = 1283
keycode 63, table 12 = 1284
keycode 64, table 12 = 1285
keycode 65, table 12 = 1286
keycode 66, table 12 = 1287
keycode 67, table 12 = 1288
keycode 68, table 12 = 1289
keycode 69, table 12 = 520
keycode 71, table 12 = 775
keycode 72, table 12 = 776
keycode 73, table 12 = 777
keycode 74, table 12 = 779
keycode 75, table 12 = 772
keycode 76, table 12 = 773
keycode 77, table 12 = 774
keycode 78, table 12 = 778
keycode 79, table 12 = 769
keycode 80, table 12 = 770
keycode 81, table 12 = 771
keycode 82, table 12 = 768
keycode 83, table 12 = 524
keycode 84, table 12 = 518
keycode 86, table 12 = 512
keycode 87, table 12 = 1290
keycode 88, table 12 = 1291
keycode 96, table 12 = 782
keycode 97, table 12 = 1794
keycode 98, table 12 = 781
keycode 99, table 12 = 512
keycode 100, table 12 = 1793
keycode 101, table 12 = 517
keycode 102, table 12 = 276
keycode 103, table 12 = 1539
keycode 104, table 12 = 280
keycode 105, table 12 = 1537
keycode 106, table 12 = 1538
keycode 107, table 12 = 279
keycode 108, table 12 = 1536
keycode 109, table 12 = 281
keycode 110, table 12 = 277
keycode 111, table 12 = 524
keycode 119, table 12 = 285

Changed 702 keys and 26 strings.
(No change in compose definitions.)

```

After typing this, the keyboard layout is still set to US.

FWIW, this Xubuntu-based liveCD from BitDefender runs Ubuntu 9.10.

---

### Post by littlebigman on 2010-08-14
For those having the same problem: (on the liveCD I had at least) "setxkbmap" must be run as non-root, while "loadkeys" must be run as root.

---

### Post by simosx on 2010-08-15
> **littlebigman said:**
> For those having the same problem: (on the liveCD I had at least) "setxkbmap" must be run as non-root, while "loadkeys" must be run as root.

Nice. Since this solved your problem, could you mark this thread as SOLVED;

---

