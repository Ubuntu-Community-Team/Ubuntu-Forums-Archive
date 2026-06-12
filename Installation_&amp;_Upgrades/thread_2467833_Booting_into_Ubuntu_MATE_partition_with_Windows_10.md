---
title: "Booting into Ubuntu MATE partition with Windows 10 as main OS"
date: 2021-10-09
forum: Installation &amp; Upgrades
---

### Post by captaincyril on 2021-10-09
Hello,

I have Windows 10 as the main OS on C: and it was upgraded from Windows 7. I have installed Ubuntu MATE on the 100 GB partition that is shaded below. The only way I can boot into it is by inserting a USB stick with Ubuntu-MATE installer on it that has a grub updated from within the Ubuntu MATE on that shaded partition.

The system does not run on EUFI nor it has Secure Boot enabled. If I enable any of them nothing runs not even Windows.

When I installed Ubuntu MATE I chose **Custom **instead of **Ubuntu alongside Windows **because the latter did not prompt me with any screen where to install the OS.

I wish to be prompted with Windows 10 or Ubuntu MATE on boot without the USB stick because the USB stick (SanDisk) is getting really hot.

Should I crated a 512 MB partition on the HD and then install a grub there? I didn't have any problems installing MATE on two other laptops alongside Windows Vista on them. Is Windows 10 special?

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAABTwAAABgCAYAAAAw5728AAAgAElEQVR4Ae2d7XHrOLOEFZcDUhw3BIfwRuFfm8JG4CQ2A94akg0MhgBIyZQtks9WncU3MGg0BmCLkm///fff8L///W wkH9gAAfgAByAA3AADsABOAAH4IBx4PZ/N/6BARyAA5fgAOce5x4cOAcHhmFI2ubNFhXB8xwLywZlHeEAHIADcAAOwAE4AAf24gCCJ4IvHIADV HAXn6TfjiD4cDfcqAqeFom/4HAUREw0d7 8R8IgAAInB0B/N3ZV5j5gcDfI6A7VRQ6/t4yLAABEACBnyGgexT 7Wc40hoE3gUB7WkJzWaX4ukNT8u83f6Pf2BwSA6I5PCYPYwfgwNn5wD Do6fnePM7 85bn5mvFOFr/JO9yx7ZuAfGMABOHBMDugeVRM8OX/ /vxhDViDRzmgPS2R0 4qiiN4InAeUuCMm0Akny7iOImID2k4AQfOwwH83XnWkn3JWr4rB8zPjHcqBE/EXcRtOHAyDugeheDJGfyuZzB2PcZN7WmJnAieiJynEDm9IxDJETwfcw4eQ JgBweOwQH83THWif3EOh2ZA ZnEDyP fYabx2ybnCgzwHdoxA8OaePfE5je av9jSCJ0Ln6YRObXSRHMEzb3xhQwgmcOBcHMDfnWs92Z s5ztywPwMgmdfNEFUAh84cEwO6B6F4Mn5 47nLzY9zkvtaQRPBE8ETzhwWg5wODx OIDZMTHToc4HPMdcP/Yd63YEDiB4HlPIQYBj3eDAOgd0j0Lw5Dw wnmMjes81Z5G8ETsOq3YJZIjAKw7BJwmGMGBY3MAf3fs9WP/sX5H4ID5Gd7wXBdOEJfACA4cjwO6RyF4ch4f4TzGxnWeak8jeCJ4InjCgdNygMNg/TAAo3NgpEOdD3jOsZ7sS9bxHTmA4Hk8EQfhjTWDA9s4oHsUgifn7zuev9j0OC 1p73g e //w72j7/SjgB2CgFMJEcAeNxB4FTBDA4ciwP4u2OtF/uL9ToiB8zP8IbnNvEEkQmc4MCxOKB7FIIn5/MRz2dsXvJWexrBE3HzFOJmbZOL5AieSwdQw4s8cIIDx UA/u64a8e Y 2OwgHzMwiexxJxEN1YLziwjQO6RyF4ciYf5UzGzj5XtacRPBE8ETzhwGk5wEHQPwjA5zz46FDnA57zrCn7k7V8Nw4geG4TThCYwAkOHI8DukcheHL2vtvZiz3PcVJ7GsETseu0YpdIjgDwnJPAuYIbHDgOB/B3x1kr9hVrdVQOmJ/hDc/jCTmIb6wZHFjngO5RCJ6c0Uc9o7G75K72NIIngieCJxw4LQdw/KXjB4/z4qFDnQ94zrvG7F/W9q85gOC5LpogLIERHDgmB3SPQvDkrP3rs5bx9 Gg9jSCJ2LXacUukRwBYB ngfMFRzjwvhzA373v2rBvWJuzcMD8DG94HlPMQYRj3eBAnwO6RyF4cmaf5cyjy0p7uCpyoR/m8AAzCAA3AADsABOAAH4AAcuDIHaoLnlfFg7vgDOHAuDkTBk/U91/qyntdbz67gaZcaVSD8Dyz Ox4G5tTg8fHWDX/DmsGBxzmgS9w///wz8A8M4AAceAUHaoIn96zH/TVnHJjBgffjgN2jouCJf3u/dWLvsCZbOWB7WnVtL//777/jv5tlIhRBJJHjyCE8hsdH5i 2w99HOGD zv69QuSgT8QzOAAHjAP2H4IAZ9MjZxN14ctROGB3KPwbfD0KX7Fznau2p4XTJsFTD1OE13sV ChrbkQWqS00u2t5R5kPdrLX4AAcaHGg5du8MNVqSz68ggNwYCsHvE8xv7MmCGztl3pwEA7Agb/kQO0ehX Dk3/JScb Gf9qe1rakJWtvuFpC8B/IPDuCIjUPcHz3eeAfSAAAiCwBYHo7 yc9uKELk69vtbOdsr7dx/wAZ z7y/vU2yuWwSBHiaUgQAIgMC7IBDvUfi3d1kZ7ACB5xCIe1pp6w3B8zlMafVmCIjUFupBtJb3ZmZjDgiAAAg8jED0bebzvDghH9jqmHLEuhY3LB9 wI/oU4wXCAK9XUMZCIDAkRCI9yj825FWD1tBYIlA3NNKW00EzyVe5BwQAZHaQj2s1fIOODVMBgEQAIECgejbojghH1g02phYa0s5YliPSvDjHPywdfQfotiaIwj0mE8ZCIDAkRCI9yj825FWD1tBYIlA3NNKW00EzyVe5BwQAZHaQj1w1fIOODVMBgEQAIECgejbojghH1g02pBYa0f5OcSsFhVYX9ZX3DAuIHgKDUIQAIGzIRDvUQieZ1th5nM1BOKeVtpwQPC8GhtOOl R2kI9tNXyTjp9pgUCIHAhBKJvi KEfOAjkKy1oRwxrMcn HEufth6Inj2GE8ZCIDAkRGI9ygEzyOvJraDwPIPWGuPGzbPCZ5f9 F2u7l/9 Fr Bruc979S7Arz8qHYai2 x4 P3xfLv7xOXx/fw4fxVi34ePz2zpL492snoYch1EfH8NY1ZXlqGvv p/6Vq16nWl sjuMIXuDTeqR8DUIiNQW6sGrlhdH//78cDwWt1ytKmddeTU68yZvhGFtnK 7cXbeJ9U yQQBEACBCYHo26I4IR 4Fa 1 pSfS8yKvGB9Wd8aJ34ueNbv0OU9O468d9rdx3Q/b9757TGFu9jeK0B/IPCOCMR71OOC5 xbDve8X/fL7pH1HZfrBza5M2DuZe2ZXINxHgiJY4RxTytt1j8ueOrC4HbG1z0ImiqbxaLxctNrN MoAhaXIbVbOBS/Yb3o2MqPizXXc/1q/JvsT6KqhCj1PaVV39tby4sjk94fAZHaQj281fL8yJMjuw15uWchXxnintKjmC4u J7K MSBXG8xzvA1fC6U JlbbqyyV1IgAAIgMCEQfZv5PC9OyAdabR v4Uc5YleNF8qDH9fkh6279ynGhz0EAd2R8z1bTKuE8zPET65FxX1Mdzp371 Oyl1siQk5IHA BOI9ag//dgyUSi0jv0CWn1uPMY9tVhZngHspLp0rerEpZfh OQ88Gu8ej3taabP7YcFTlxUv8mUAtIlMgNQbkG1xMLebYtW mxeUaayPj kNvWTPSNyP4WN8a9QLoXG02dbi4iOb1U7zyU5gEq/m8optRXkckvTLEBCpLdQDWi0vGaC1Cw7Or1 Vj6mDVmTmkPptjFNrPY2duVarQx4IgAAIRN8WxQn5QIXPIrbWnvJrimHiE t/3vW3tX2F4DkM8Z4tNi3D6U7kPpReVlnJadzHinv/sgvuYktMyAGBsyEQ71HXFTz1Zru0jzOtdOMM0DP6PFX/7B9nz3kQEXnfdNzTSpvFDwue/mvpSWR0c08i0f0 fhU91ZGCfqt8bXhun9r6t98kGC0uKLMYeb9PX22fyTv28fE5fI5fS lt3prgOaSvHk/dBcFTtqSNooubRKp6nw4eoi9CQKS2UA9htTwNL66lpZwLlD/ydgNn1V8KZ46I9 ovjjPWn/tXXe2tat00ABEQAIGrIxB9WxQnLC0/ CxWa 0pP6/YZZxhfVnf1wie4Z6te7W Zj7f9SV2pp/PsotRo27Tx4X7WGofnye4izUhpAAEzopAvEftKni2fJWeKz8 8s/1eX k8tkfTs H0hqcpqH 1bbarrVya9rG0Pe1GruwcXx1svITcRtsD/2lnymM bf4MtsGzWXuQ8/ZrWdy5Y/1OA9axHn7/LinlTbDHxc8x33Q 91DbST7HRy3OVfb5UuQiDkiuyC8Pu2dx7l/ud/cyUp T62fVqy UQrSp6 06zdBNXZec9UfRaq4SXI1Yi9GQKS2UA9qtTyZUaybMi0Ma6h6unQX3PTtFJ/5KtGyy8MwlsZWW3VJCAIgAAIegejbzOd5cUI 0Ld5JL7WnnLEsB6f4Mfx WFr6H2KrfdegoDuVYv7VLgTSfSs3olC3Sofw30sCZ4SV2/znT72Naer41YHIhMEQOBoCMR71F7 LX1FXA5EOoalZ98iUUcKyqsrldrUw s1amnwkpyqqL4nWaSd QqVP1rK MaW /4hJa1f ztktnkQHq39KKOy1JcxtxmMuFiUwpwrlO7n7Sr5ROdWf7x7583CrM6UWb1JjIuyAQ97TSZt9TgqcmJuI1hc0GO9baFeQV4ePm8ptEZPyc/sCRDdsVmsYJ9AXPyXQ5BXuDs/IphfUj5f89uhpcgrrAhfi4BIbaEetmp5skIcjBRdy49cV38pDM61e2FPjeZIaBuLSYMACICAIRB9WxQn5AOfQWutLeXHF7N6vGB9WV/jh/Hg1YJnun/pHh3eGKrenxp1q5yOdyq1XTxPhNaxXSgmCQIgcHwE4j1qN8Fz1iT0okwKJ3Fiegtydn565jTdY Hv5K/Gul6zkB4xfbu03662TivaRsd b6/vuW9D23aJiQkjfRhlc9b8vb9W3lbNJfhy2T/Dn6bQyh8rhD5SIyJvh0Dc00qboT8SPK2DKknmzVIIlwGWWjvlFe1Ebk/4sa95AzlHMP2ep3cAPfHRb0AZVzqR9CmN/nq2nEBhy9zm4z7c7XdDizL1S/hqBERqC/XAVstLdmgtg9ebnHadN JnaJK6HCMzXxOHN yF1MFct9t/qkwEBEDgqghE3xbFCfnAR/FZa0c5YliPU/DjPPywtXyN4Fnes/WgPN6Zwn1JZboTKV2rW VlvI81nydCa 5iARCSIHA BOI9ai/BU8 K6TnQQzf7lvg2ptWVf5O/S4LfnDGVfwyfX9PLXepjrZ0ffop7wTO/wSj9ome/ypKNc drNrRsV39VrKr Op8fd/vpwjXNJZ4BAX9hk z7Vo4LOQ8cGO8djXtaabP6YcHz /M 5J/YFPGCQDSTwxN4S7sq8auEN9O94Kk3Om9D6QCCXcU6LQVPbdhsd3AK6S3P8qvtsts ochti8FIvBgBkdpCPXTV8rwZCwcXeLuFs76/KT7viXQaaI94zsx/pT2MN9mj34Nd9kwOCIAACBgC0bdFcUI 8BG01tpQfh4xq8YL1pf19bwwPrxC8Czv2bofTXd13aV1j1Z6uk7163rbczzcx1rPE9zFMmTEQOAiCMR71F6CZxIq9bKU4fn1OWkns6 RViEfN/q84IdUlh8nJ6FzernL6Rtr7RbruaJtyE/W7FdZFBrXbJjbLWxXfw MJVy2aS7hDBj13fCTi8F2vXWqc4hn8wWB3jYj7mmlzeAnBM/y9zurX/GN5HFvgubXlt1mnaETiUWyMTtthvw7mpOjKAVPEVSOYSFmLZZHG971634nYqquOk6Emud2Kzbnff6h3uWcFsOS8RIERGoL9eBWy4uDi3PipedeLKtyPXaYuO4444TyYpxinwQ V/olCwRAAAQMgejbojghH7gVrbX6lCOG9bgEP87HD1vT3QRPfU1xDMM9Od2pb8P0MOxfHNAdfH6ZoVu3ztDpHjffx1rPE9zF6uCRCwInRiDeo54WPJ1/S8 QC18z z35sFms0HNmaqfyuc UP66DPvSpvNnYbRcXUX7VPaem9i1f6fx2mFuyMfUx6Sopf8320F961lZ FFeVv9Bs4jyndHEGzFWEu57Jx1DjzPOY7OfZvI7qe bGPa20Wfuw4PmeU8SqqyMgUluoh69a3u/g9LiD5BOk31kZRgGBMyAQfVsUJ QDba4 Xps75ecTq/w6s76sr dDjLf4Yfk/FzzjaH Rfuw xl3sL9aIMUHg9xGI96jHBc/ft5kRDYFZ JVAuQrK2hnghOQgonIerIL7VhXinlbajLyA4DkT3X0CU7yd VZLhTHPIiBSW6gLfC3v2f5pBwIgAALvgkD0bVGckA9U Kzda 0pR0zrcQt HJcftnbnEDx7DKUMBEDgqgjEe9T5BM T6h/zG57lG6RXZTHz9gjEPa201bmA4OmhIH5WBERqC/WQVcs76/yZFwiAwHUQiL4tihOWlh98FpW19pQfV8wyTrB rF/PNxg/EDx7CFEGAiBwZATiPep8gueRV6du /TGZf57LfVa5F4VgbinlTY8EDyvyoqTzVuktlAPcrW8k02b6YAACFwQgejbojghH3hBaMYpr82fcsS 3t6AH9MHJgiePZZQBgIgcGQE4j0KwfPIq4ntILD8 wba44YNgicMOQUCIrWFelip5Z1iskwCBEDg0ghE32Y z4sT8oFXBGlt7pQjdvb2BfyY GE4eJ9imCEI9JhDGQiAwJEQiPco/NuRVg9bQWCJQNzTSltNBM8lXuQcEAGR2kI9sNTyDjg1TAYBEACBAoHo26I4IR9YNLpAYm3elCN29rYB/Mj8MCwQPHtsoQwEQODICMR7FILnkVcT20HgVW94ft2HLX/85/vzY7iFv6SVfoMh/DWsYrHmH6W96Y8NpT6WP8J7/ypazonWX Wy/I/h83sYsh23IY1zuw0fn5/DXePOYfpx3HHeqn8fqkPXzCHvpQjEg8sGq XVjKhxdFjw2/8Vt9tQ51zJqcQZG9TxpsiPBsH7iAhpEACBgED0bVGcaAo3C7/W8U1bfFarTis/zGP4sb LHbbTTUzmJpRnsauGIvhcCx9b7z0Fz8U9q UjWvmelK06rXzf1uI/9js8X0RISYPA0RCI96inBc/R7yz1gKwxTJqDx2f0h0FnkKZSli37Tf3gxxIUREDAEIh7Wmkre INz1n4ud H 62zEUfs50tBEisnQagr Fi7cROXDuLrrrGyYDkOMdZV2Zgz/2 q9/ERxanQfqwd82J67jKO9f05fKJ4etD/LC5SW6gHs1re0kBb65sT5Vv8/hq tNaRB q04IPjUFHf5audwrEevBcchCAAAnUEom L4oR8YG7d9mv5HPe yeI6V31 7nEYWnVa b7tXud86LORXOJRVqT8WmJeufr8Aaca/y1vP8HTfIK/Z7V8RCvfr1irTivft93L79hYHwPPFwFbkiBwIATiPepxwbN1r9qodTisTOSUNmJCaeulmtSE58UEBREQEAJxTytt5U8InurWXy6UV4a2ge fn8NHEjy/hnuKl3VzanIg7c0 XTTsDc3pv5gO V9 fCur1Y95Ma2h7k4Y0ziE74CASG2hLu 1vGjrkqOqYRzQA7/yFPbKVMd4PImX/iCz0pieWsB7IUcIAiDQRyD6tihOyAdaLz5eipTz253usE2 yd5YqOV7s1p1Wvm 7bCXvys6rSbK S rUI7YuWRFzrkqP2zeewmei3tWy0e08vNyTN WqfmmLW138zvzMwLPF35liIPAoRCI96jHBU9NNz4TbtE61NbCsv3XvXzxxdec4nvdn/BjS2zJOTICcU8rbXN6neBpnz7YpcRCiZzjhcTeDJ2/Eq58j 74qUVLaLKK8waV4BkuObmrXM8 LdEnJ4v2Y4Ncd2of0 rV8n1fyif8awREagv1gFLLK yscTRVsLVu8LDJudS4OMCSiDAXx/SYDe89eMRBAAQ6CETfFsUJ UCFuavSry180ezbWvm5n8oHNw 0nb7F0fCv4yDhDN7kc711U3w5/7IO5YidJSPK1JX5YXPfRfCs3LNa/qWV71elVaeV79vu53eyf L5okCYBAgcBoF4j9pN8BzvKytah0fp6 40iknM1M/sZe3CNeB50YFBFAQyAnFPK201XiR42oadP6GwjSlh05yA 93O8qIwG zrz2/DTRtfn3jYRUO/oWlh66EpX0hKkdPnC6SYF8fwr5dnZ Q ZFZHhH EgEhtoR5SannZvAZHUwXjQMktu1CPXNyw8AW3R96rr4k/i0MM3ifkiYAACPQRiL4tihOWlh8seyr9WkskaOX7vlp1Wvm bfFB6I/O aLXIlGff65COWJnZsMyBj/2EDzr96yWj2jl 9Vp1Wnl 7b7 R3/zNCKa2RfbnmW9s8wPF8IKUIQ E0E4j1qV8FzTetIE3U MuUpEn3HnM/zogAiBIECgbinlbZKLxE8i4uH35jxLY2YNousfhCauoLlWF9iqJ93cBRprJA/Nol5Me37nePjuP6iUqlD1q8hIFJbqAeVWp4ManJUFcJXDFK2RUYBs8Y5K6wLmjaehPv7Pf9WS oX3icoiIAACPQRiL7NfJ5/G0s cNmLnW368OVnb2kWPtQGms/YVn5hy27 rug1Jdrzn6pQjtiZyFKJwI/pAxPvUwymRwWBwhfYnp9ffijyreMHfMdP2vJ8USE7WSBwUQTiPepR/5ZhK 9V8mepPOkPKSdHzC92XqIpXp5Rq93uT0HrSHaG/HHcmBfTMs6Fo53oJA4Roi9GIO5ppW3YFwietgnKTy9HoccuOmkzzTOO6TG7tol8no9bg0lgWvqLVr2Yb33EvJie7Q2BXbz875yFYpK/iIBIbaEeVmp5MqnJUVXoCZ7j/bzmxHuf1KWOBzvA1vlq9T0PfdzK4H1GlBgIXAuB6NvM53lxQj5wiYr5kSx4xot5EhPC2ZzyfYetOq1837bwbSrwPs7Hrbzl79Q2h 25T3UoR zMbFnG4MfED8PB xRD6lFBoHnPavmIVr5fpladVr5vu5vfafmnmG Dx7yYLgxMCZ4vEhREQOAlCMR71KP LRtle7p9r4r3rNxu tB5 TyYa/C8mLEgBgJrCMQ9rbS121HwbBzi7lPd8uBvP8CMB713HsWFIYwzfoJQe9su1LPZzp82 K/VT DFujE9Q/z1OeQ/ljTZv/hq8lyV4HcREKkt1ANLLa9qVcFR1TAO APsa9AfaS957LgSLtzqqQitjn7ioSiYDr7yJxpc38UeEJfhfYCQJAhcAoHo26I4IR 4BCP4tfFMlJ9z/qaV7/1Qq04rPxizzzlfdtqe91SPcsTOkjFlCn5kfhgWPxU8C3TNL ju0/IRrfy38zvOV2qSo 32ske8l8W6MT13wPOFkCQEgV9BIN6jdhM8vb8qPqyNe990hOgv3NRHn1Iv3 f FO3RsyV zK0C0QMhEPe00jaFXxY8/Wa69d ONGHIvSmahUXboP4N0rozKEWpvFqTk4ht4qaPabUPY/c llETwl9BQKS2UA8ttbyqMXao6CKeKthaSwgIvL35NzQzVyZueW7qD1x53rg 01guAu8dGERBAARqCETfFsUJ cBl2 DXrILzOcWRVs3P/m7su1qn02c0yLW38/7xcz522E63MZnaUJ7FrhqK4HMtfGy9XyZ4GsHc3j e3wl cN4wPF/UPAd5IPCeCMR71H6CZ3hmTA4u o3KfWwUS/NzZGpag9D50OfuT9GeaRD8WA1s8o6AQNzTSpvtPxA8jzB1bLwKAiK1hXowq VdBQ/mCQIgcF4Eom L4oR84HkReGxma3hQfi0xL7KH9V uv2Gyq AZQScNAiAAAn IQLxHPS94/uEkGBoEQCAhEPe00lYBwTPBROTICIjUFurhpZZ35DliOwiAAAgYAtG3RXFCPtDq vgV0VubP VLscvzBHyuiY tO4Kn3wnEQQAEzoRAvEcheJ5pdZnLFRGIe1ppwwLB84qMOOGcRWoL9YBWyzvh1JkSCIDAxRCIvi2KE/KBCi8GT5ru2vwpv6aYJ4Kw/u31N2wQPMUUQhAAgbMhEO9RCJ5nW2HmczUE4p5W2nBA8LwaG046X5HaQj3E1PJOOn2mBQIgcCEEom L4oSl5QcvBAtT/UUE1vhFeVtMtGU6Aj4Inr 4oRgKBEDgVxGI9ygEz1 Fn8FAYHcE4p5W2gZC8Nwdbjr8CwREagv1IFHL wvbGBMEQAAE9kQg jbzeV6ckA/cc0z6AgEhsMYvyo8vdkafYmuPIKAdQAgCIHB0BOI9Cv929BXF/qsjEPe00oYLgufV2XGS YvUFuphq5Z3kukyDRAAgQsjEH1bFCfkAy8MEVN/EQJr3KL8 GKnUSf6FMtDEHjRpqJbEACBX0cg3qPwb7BAwIArsiEPe00jbIE4Ln13C/fQyf39HGVn6sV0v32vbKan3V874/P4bb/Wsq/LoPt9tt/ncf5tx6wzfK/brf8hwetev7c/iortujHfn6tjbC0cIaL b6Lxk/2yJSW6gHrlpebtHiVSs/t2zHem17Ze0eY0nmsfXnsb8Nondss386jt1Z990Gj2Pehg9zQgWv9sD4e/j8cLh fA4LV/fwnLba1Zjjw O9okG0rbPmxZq8wpYtfT5g75burE5vXr2yjf2bfx85vaF 9G1RnJAPzF21ONjKzy3bsV7bXlm7x1jS9nfwr8Dql/i35FVhRTp7y9ycov1xxNDoU2wVHxcEWn6glZ 50o712vbK2j3GktLvdHxNbLiW/tE bc3N8t2d5bZyjvzAhkfOqDUoKAeBv0Yg3qOu6d 87 j4uh/4jf3WOfq6jr1bB 3Nq1e2sX985kagdqoW97TS1v0bCp7xUI/pJ1Ax0kq4GAnsRM7vz HzYcVzB5sencY4h/tw/9i6wX/DxnKM8ZIonB d3w/ri9QW6qGqlpeHKW1fz8812jHfp49bi5hu99Is8TyO/UVeNzvpFWy1saz3O tejlmfxZY69ZZj7ohhEI6f8g9xjK12xXqW/sGHHNGMH6VL235nzX9i8B72ln2U1vTKyprbUya2b/Pv0bdFcUI MI/dsreVn1u2Y76tj1uLmG730izp Dv4twO C D7/FtyquyA8uOImeXKTam4fpb2P5Nhtd5PEIj7IKZrM13J6/idlZYvLm7NLeZb lX3hr6PeDEAdA8CuyIQ71FX92/cq6Iv3YNu Mw9UNzaR9zTSlv7SwietonTmzP2duePRblXbIr cmoOCvu1rfQ3bIxjxPS6lXvVEKkt1MW9lpfHa9nays8t2zHf1setRUy3e2mVlGsf 4vpVi 9/K19xHox3Rvj2bItY2yp0xrfDqUgdraqPpy/1a5KvV2E7IcNrjSItsV0pcmfZkX7YnqLcb02vbItfTfq2Pm04VXt6NuiOCEfmEdp2dvKzy3bMd/Wx61FTLd7aZW83t 1Rt4jP84/preM0WvTK9vSd6PORv7F1ku lTUoP54YGiUaNf4AABW1SURBVH2KregVBIG 3yl5/bup1p6v5L/y3vCkj/hdrBgNBNYRiPco/FvFl6zD Is1on0xvcWUXpte2Za G3XwmQ1g9s Oe1ppG l1gud44OpV6fxG5fi1bH39Ij3YiWQWqo0 oZzLvuwr2VPZJF5WBAoj1ULMjOr6NEYSQEe8e31NZfoK/P2rZqO 7ijbNd l7TZlu1Cpv9KO1uK7ORSfPqv FhtnW757c23NQ PEUH0q36en P1uczU8lmWfbk17uNQ5ozGnUKS2UA9XtbzcytuTcxcP6m/NY/c2WHSohd1ByKuWGR7ir/aex8XHI3ZlurlebtyPz8/ypzFc2cQXP57FyzFyqc/38Qe5PI6vfZt7z7Gp78znYajPM 5FZ7vje33fB/vHwf1 jeU PcfdGO09taxbtyfPfon/cuyMzbLsZ3t96m/q/2P4iMJ01e97G9wazL9PUF87P47bC7YvxrNKfVroyouyGbOCz37/zX185p9VKbC3doszzK/DFILYoT8oFWe4rL9thXyC/szvuhh9fndwcPx8dpnp7Psy3V9bN6zr8t9r 3e4rDP4dXsY7788 zyHPN5ytO fHETls7W7dfe8Oz4Os7 x2xOt4v/B4ry8q7jvdb1lftvtC6W8S2sqWW7/1syz/6OnNf3hc31mT8aZcNZ5SsIwSBd0Ug3qNeJng29hL3qo Be/277o5j2hX3tNI2mycFT/ew5x/80m84hgP4657fsEwY jqtuFW2slsWMu1AHgU0KyrfhjHnMT57pjHUPl gpqJ8yUj1W32F/Km9t1djuIeNNN a7e73dfxcpo7r/zdnmS4YZrsba74wFQ/NYy8dG8OcMm6hTZpH3awogoxCbrJzmnu2y/c9lSVxesRhCy6 j9ImkdpCPWDV8nKr2YaCv K18A3jVfHwdVpxG3UeT/j4tW uR7Z2au95PPeX7F WJW6Ph62fk9snizLV82PHuJ/nLOBrXkVVX2 yVzZNor/G8vWmfZ15ow6n9vqgwMKpL9 2FW/1qb7nB5TqHFRnGn9pl5W7ccNaTq2ntiXf/Xr5MYSJ8vxDiRtnLPbp2hitPRXqFhzQuDH0Y8U1n/rL2Pi6Yayn9nroP2Cc/Ze32dsQ7W3VC P4dR2b D593Ap9eupHXC9/ 3MqS29xjnh4Lli5T3tbczz6tihOyAcqTP4n Qv5OgvFOT H1p7xdVpx4bHnue3HiutpZY7rlbUo956ru8BfGPvxQv/wTyClszZlhEjmXyiYk5S/rxhqa7OP4Ol9jY8fz 9kFk8 oefjVda 60xnez43c 85Fv2QMMs1yrNH fHe4Hye949NX bHjWeBla2fUbKEEATeFYF4j3pO8PQ zce1V3t7Scj4Oq241bUy7lX6GzKl5iAshZPHv H/xiZreJf9yK /4l7vZ0D8OQTinlbaentS8BQBvEGONOMDtN/4ekNmOjizaKF XFt/GI/d zLL8GmL6 D9Gu5VwcLX8fbmT2EnAvt6rq95LuWlxNuQ 8nz0nxDvcL2OJdgm0vapvbjj5tcu260Txi4Rt2x nNdzsP36 PWj19nb0dv7r0y6z Ujw lGkec8XYMg0htoR6ianm5VRgjFbj8t axs9NsH22dsalwIolCvbKIe8IkRmxsrYeFft0be9zGLfans3 0yfen/ePHdfV9dmGzq7OpT9dRBRdXuuSkFdZ4OY/r9 uCz4XNfhRnf8r2H3DEcp/28dG48g3aYsxYd3qjRC4lDV1ErI1fI7/msT f9vE1uxqYFrarD43vfPVmex8Zx/sbPxcfl00b9l91Ln4Mv97FhIpE9G1RnLC0/ODUMNqr7lx b8/UuF7MxfUzdt1LW9mW9VMd69DawL/8ByM7 FZ8WfL/xZoJ18f5Zy1Lfo2LXvyP8vcVM7eu3z6Cp eXKOL4 /Z p2J/b49ZWeuu4/dfpQ hU71b LapokUclinfnyOx3KctLj/rztLemowvWVQwSWMTAYFjIBDvUc8JnrW94PZYby9xr3J/ALvhiwoqWZ3WPfD49/piqiSeQiDuaaWtsxcKnjpEnc3FAd86kJ2jGJv20xIDFbrR5qjfRMtSLx6qD4W 9liv laZxKbKfBcXkf5c/Hg5bm38Bld8Hq/ANLdaXoLKsTVHhWPLZlXx8v /Ql/fFju066sMlzphxNpLZQD1q1vNwqjqkSl1 MrfK43t4m1/bBtdc6KHSjzVHr23PMj2VVzI75rceK3emBt1e2sHlpxZQTx3b1iv4dNpbfeggo2ri imhrTJ/v4pv69AM4/Hx2iru La/o381zrm/rWH8L1SqEvlpjLMaJ7Xzax2tj HIfHwfJ3Em2xEhs48tjmU/7uLXppJuYxjbTG34mKvf3S 0i2lu7OE4v3Skr5jHhlPZfb/5jVevX73OPc45H32Y z4sT8oG5RbRXJS6/YvdYq8j3XHdtN80rr4fWTaGsyWHEwY Va02xWObTPm61O lN85xGlN0Ko0XLcVyNzeN0bN08j2ncvfm35JebH2JouoOUqOTUEfCLPsWsf50gUPF5m/ZJb4 YxWW59qvCvCKKWX1vS9letcrzf8pNe8zsbt11vD3F/FLPnbtFwxbfp7op o7tyrSwUDh2UbRXpwqtvcdI YQgcCwE4j0K/ bXr/QTpS/tlVkfrrzwJa374zSufJBCb80Ud/3Gws3jxD582sdtAJcu p tSd8qdvXGoloanxmX7BXpuKeVtrFeI3iOJPGvEM/Tsk8zdBEYyaMHIE8OH7d2K2nr56P318v9BrPuPt0nClbm7FzpK2/Cmk2un7SKtXqac21uqWGOeMxS7mT39EZWmEOqszJ2mqvfhNamNo/UaYjEMXxxLPNpH7c2nbSff8EZP9aL3vB8Zx5HzApsDE995TsKPGtlnp8lxjkV1yuXjG8mNPd4tsn2UvlV2jXetcb0 TG 1qez26Lzp63Fm47pr7T7vue61XnmPvv ooZzGGPmX7bH73vZq35qbVU2Ts698Wl1HTYjd7wfyHPIsdh/Lunu38jTXrq51ytjJ//l59izyZVtHieO69M bn37tMUz18uHY18vtpv3qnjlTI5RHeIWmjARxYmloBLHVY8 f7K7fDu5x/XY1q FL2vN84Fzu8BXtivsjdUrC3Zt5oXWqWd/HFe2bsUz2DY29336eKxrZa/j35Jbbm6InacQO21Fo0 xvJcIAuPedueR6LRpP/b2gXUUylfPDTtje34sGbeyx/L W9511H/j7r5p3rKjMscZz3xvCBg0MfF3gMmHLM4CG27E8HOYfw7bG0IcBA6FQLxH4d/88vX8Rq/M nDlj/izVf/s vWmjkNu0ZeCbWMfvk8fj3WtLPv1V9zrR3P4348QiHtaaev0RYKnRBa9jaivqE4H/PiV6UKkLElmn5SOdcYTuywrNtIMy1g/n 4LsLLwYEUTadPXtkO7RV 2WdMblvlCUNrYmu a7a7cOwU3AxundukYL1HJ9nJOyi5tdGON/c9rocoa0xxOmu 8bg3bamuhbpZlfnwftxa9dIszeSSLidQW6oGslpdbxTFVEvJrePgfmn8XHqff4ZvnUditC/Z6WcGZp9a9s15uL5U/5N/aP1oTC8O6pCKf7 ONPptzqmHjfitnMX5jnm6O av wa5FX5qM1XM M67pCIPzR/d7EDH9OvfGnMqmHwufxktuoIlP7E82j0Y5O2I6tuulG5g28Bq5mgz39kQbYtn2cYr9EOzolU2XIa3l1nUxmpe/Sx0tVzr6tihOyAeq/rb909gzb PvPI55Zsu5eY75uLXppbfzYuzJ7ikX49 SV34d Jr7mfCJPsVW jWCwLv7HfnxKUz38d4dy90DyrtOzf/k/id38pgfmnxa7iN/kKy9WRvT 9J5vOjLivk5X7fxjNLohCDwrgjEe9Q1/Zv3BX6len6jV2Z9 PLH/NmV7/UefeLPIRD3tNLW2xOC53NGvLKVbZB4Vhfj2cG94a0Za7PaV9Hxfom/GnfLDN7ZNtkvUluoh45anuq/Y7iK8wM83mN q/b8ZJDxMp0/QPhJV4 0femcHjHkT v6y0hpyJHwOZKtJcqtlF0MW5fPsk30bVGckA8sW71XanX9ftnfPYrOqv2Pdvjn9fv8W MU5cf/zU5PwehTrOxxQcD3 B7x1X27t9/5o7vOa9Du 4jXjEmvIPAaBOI9Cv/2Gpwf6XXVPz/S2VvUxWf 5jLEPa202XB8wXPj5aR8I7IB/8a Gq1/kG0CxO LP9sMfmfb8gxEagv14FXLyy3eLLaRe5t4vMvUXrvudqiln7fYxd4tnbx2TlsseI86hkNNWDsQPhv3y3vgvc2KcU90P7nL/UTfFsUJ cDc4s1iG9fv9/zdg/hstP/BXv 0 iP8i4au8Y3y44mh0afYmh9eENi4b/f0O39z14k7dJ/0T3zEPhbQCwjsh0C8R Hf9sP2qZ42 uen v6jRvjM3wU 7mmlzYoDC56mmtvXOGoP7o8CvGdfj45N/T0QEKkt1MNVLW Psfbt4yrc0zz11at3Ffj3Xd337K0leL6ntaVV4tEefr/s Uip6NuiOCEfaHPy8b f49HX7 j278 ANX5RfjyxU37D/yE0yzuuIPCb 1ZjcdfZ39vQIwjsh0C8R Hf9sP2sZ7kM699r38MM2rXEIh7Wmmre2DBszZV8q6KgEhtoR6wanlXxYd5gwAInAeB6NvM53lxQj5QYWvmlB9TjNJ6sn6sn7hQC3/CD2vrfYr1f1xBoIYOeSAAAldGIN6j8G9XZgNzPwMCcU8rbXND8DzDCjOHJ/5oEaCBAAiAwDER0CFuoQkTUZxQXm92Vqf3H XgAz/aCFxhfyB4ttefEhAAgWMjEO9RCJ7HXk sB4G4p5U2ZBA84ccpEBCpLdSDSC3vFJNlEiAAApdGIPo283lenJAPbIFEOWJmixuWDz/gR/QpxgsEgd6uoQwEQOBICMR7FP7tSKuHrSCwRCDuaaWtJoLnEi9yDoiASG2hHtZqeQecGiaDAAiAQIFA9G1RnJAPLBrNiV6ZVaEcsavGG XBj2vww9bZf4hi648goF1ACAIgcHQE4j0K/3b0FcX qyMQ97TShguC59XZcZL5i9QW6oGslneS6TINEACBCyMQfVsUJ QDI0StfNWj/BpiltY7hqw/6y9OGBcQPIUGIQiAwNkQiPcoBM zrTDzuRoCcU8rbTggeF6NDSedr0htoR7aanknnT7TAgEQuBAC0bdFcUI 0ENSy6M8IwA iH2ZDcvY1fhh80XwXPKAHBAAgXMgEO9RCJ7nWFdmcV0E4p5W2hBB8LwuL041c5HaQj2Y1PJONWkmAwIgcEkEom L4oR8oMCJaeUrpByxT1yohfDjevywNUfwrO0G8kAABM6AQLxHIXieYVWZw5URiHtaacMEwfPKzDjR3EVqC/VwVss70ZSZCgiAwEURiL4tihPygQaPj9fgovx6YpbnAevP ns KG68QPAUGoQgAAJnQyDeoxA8z7bCzOdqCMQ9rbThgOB5NTacdL4itYV6gKvlnXT6TAsEQOBCCETfFsUJ UCFLWgoR xqccPy4cd1 WFrj DZ2x2UgQAIHBmBeI9C8DzyamI7CAxD3NNKGzYInjDkFAiI1BbqIa2Wd4rJMgkQAIFLIxB9WxQnLC0/2AKK8uuKWcYJ1p/1b/kG8QPBs4cQZSAAAkdGIN6jEDyPvJrYDgIInnDgAgjEg8umXMu7ABRMEQRA4OQIRN9m4pUXJxCzELN6WwB wI81fkSfYvURBHqoUQYCIHAkBOI9Cv92pNXDVhBYIhD3tNJWkzc8l3iRc0AERGoL9TBXyzvg1DAZBEAABAoEom L4oR8YNFoTvTKrArliGE13igPflyDH7bO/kMUW38EAe0CQhAAgaMjEO9R Lejryj2Xx2BuKeVNlwQPK/OjpPMX6S2UA9ktbyTTJdpgAAIXBiB6NuiOCEfGCFq5ase5dcQs7TeMWT9WX9xwriA4Ck0CEEABM6GQLxHIXiebYWZz9UQiHtaacMBwfNqbDjpfEVqC/XQVss76fSZFgiAwIUQiL4tihPygR6SWh7lGQHwQezLbFjGrsYPmy C55IH5IAACJwDgXiPQvA8x7oyi siEPe00oYIgud1eXGqmYvUFurBpJZ3qkkzGRAAgUsiEH1bFCfkAwVOTCtfIeWIfeJCLYQf1 OHrTmCZ203kAcCIHAGBOI9CsHzDKvKHK6MQNzTShsmCJ5XZsaJ5i5SW6iHs1reiabMVEAABC6KQPRtUZyQDzR4fLwGF XXE7M8D1h/1t/zQXHjBYKn0CAEARA4GwLxHoXgebYVZj5XQyDuaaUNBwTPq7HhpPMVqS3UA1wt76TTZ1ogAAIXQiD6tihOyAcqbEFDOWJXixuWDz uyw9bewTP3u6gDARA4MgIxHsUgueRVxPbQWAY4p5W2rBB8IQhp0BApLZQD2m1vFNMlkmAAAhcGoHo26I4YWn5wRZQlF9XzDJOsP6sf8s3iB8Inj2EKAMBEDgyAvEeheB55NXEdhBA8IQDF0AgHlw25VreBaBgiiAAAidHIPo2E6 8OIGYhZjV2wLwA36s8SP6FKuPINBDjTIQAIEjIRDvUfi3I60etoLAEoG4p5W2mqtveC67IwcE3g8BkdpCPcz5vPezGItAAARA4DkEvG8zfxfFCeURTtiAAzjAgcc54D9EMU 1Jgg8581oBQIgAAK/j0C8R Hffn8NGBEE9kQg7mmlbYxVwVOVCf8r3hgEj/fFwx5s7D/W6H3XiLVhbeDAPhyQkOPFCeL/FG 8ggd4wIGfccDuVGuCAD59H58OjuAIB36XA3aPwr/9LuZwHLxfyQHb0 ofwfM/yCYynClE8ITXZ Izc4HPPQ4geP5MyEEIAz84sM4BBE/Ood45RBn8ODIHEDzh75H5i 1L/iJ4InImxfusGwTBc7nxz7rWzIu1vjoHEDzXxRoELTCCAz/jAIInZ 3Vz1rmf949gOB53rVl315zbVcFTz08ET7 e0dgBmZwAA7AATjw2xwwMYL/QAAEQOCVCMSvfP62n2M8zlY4AAdexQH8G9x6Fbfo92 4JbHb7kWL3/BUIeE1FXHWnXWHA3AADsABOAAH4AAc8ByIggDp2 J3/8AETODAOTjgfR9xzkI4cFwOIHjy9fbTf70dB3VcB8XasXZwAA7AATgAB96DAwg55xByWEfWEQ6sc4Bz5z3OHdaBdfgpBxA8ETwRPOEAHIADcAAOwAE4AAfgAByAA3AADsABOAAH4MBpOFAInvy wN/8vgC4gzscgANwAA7AATgAB AAHIADcAAOwAE4AAfgABzYhwNVwfOnr43SnleP4QAcgANwAA7AATgAB AAHIADcAAOwAE4AAfgABz4Cw54wfP/AVPZLsdysyvcAAAAAElFTkSuQmCC[/IMG]

Thank you!

---

### Post by oldfred on 2021-10-09
Windows only boots in BIOS mode from MBR partitioned drives.
Windows only boots in UEFI mode from gpt partitioned drives.
You cannot really mix modes on same drive, and should not mix modes even if different drives.
Or all systems must be UEFI or all BIOS.
If UEFI hardware generally better to use UEFI, but you cannot easily convert Windows & change from MBR to gpt will normally totally erase drive.
Always have good backups.

Post this:
sudo parted -l

Grub from Ubuntu will offer to Boot Windows if installed in same boot mode & it is a working Windows.
But Windows cannot be hibernated nor need chkdsk. If BIOS, you have only one MBR, so only have one boot loader in MBR.
So have both Windows repair/recovery flash drive & Ubuntu live installer to make repairs.

---

### Post by captaincyril on 2021-10-09
Windows is running in BIOS mode. That's how I received the PC. It had Windows 7 on it. If I put UEFI in BIOS nothing works at all.

---

### Post by captaincyril on 2021-10-09
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1574MB  1573MB  primary   ntfs         boot
 2      1574MB  445GB   444GB   primary   ntfs
 3      445GB   982GB   537GB   extended               lba
 6      445GB   553GB   107GB   logical   ext4
 5      553GB   982GB   429GB   logical   ntfs
 4      982GB   1000GB  18.0GB  primary   ntfs




Model: SanDisk Ultra USB 3.0 (scsi)
Disk /dev/sdb: 61.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  61.5GB  61.5GB  primary  xfs          boot




Model: SD SD128 (sd/mmc)
Disk /dev/mmcblk0: 126GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      16.8MB  126GB  126GB  primary

---

### Post by oldfred on 2021-10-09
If it did not show partitions during install, you probably then had Windows fast start up still on.
With BIOS, you have to temporarily reinstall the Windows boot loader to MBR, so you can boot Windows & turn off fast startup or make other repairs. Then you have to reinstall grub to MBR and with a sudo update-grub, it should add Windows to grub menu, so you can dual boot.

If not post this, Boot-Repair is primarily for Linux issues. Its advanced mode may let you install a Windows type boot loader to MBR, but only Windows can install the Windows boot loader:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by captaincyril on 2021-10-10
Thank you for the your help, @oldfred.

Just for confirmation: With Boot Loader (MBR), Ubuntu cannot launch, right? The only way is to have grub installed in MBR, right?

I tried to remove quickstart from BIOS but it was for Diagnostics. I need some time to work this through. I will keep the thread open.

---

### Post by yancek on 2021-10-10
>  Just for confirmation: With Boot Loader (MBR), Ubuntu cannot launch,  right? The only way is to have grub installed in MBR, right?


The above quote doesn't make any sense.  Grub is a bootloader for Linux as BCD is a bootloader for current windows.  What oldfred is saying is that you can only have boot code of one bootloader in the MBR, so EITHER grub or bcd.  The advantage of using Grub is that it can boot windows also.  The disadvantage of using BCD is that it won't boot Ubuntu. (Weli, that isn't totally accurate as it is possible to boot some Linux from BCD but it is so convoluted I'm not going to discuss it)

If you can't find the quick start or fadtboot options in the BIOS firmware, look in the Control Panel in windows for a section called Power Settings and turn off hibernation if it is on.  If you have this setting an turn it off, it will be turned back on during some major updates in windows.  Of course, the standard practice here will be to not bother to ask the user if s/he wants it on no will the user be informed that it is being turned on.

Good Luck.

---

### Post by ubfan1 on 2021-10-10
Check your BIOS/UEFI Settings for selecting the boot mode (legacy or UEFI). Some machines let your set a preference, and will boot the first mode possible, so in that case set your preference to "legacy before UEFI".  Other machines may only offer a settings, UEFI or compatibility, so compatibility or CSM is what should be selected.  Sounds like you have a machine with only a legacy Windows installed, but the preferred mode was UEFI, so the Ubuntu boot media, which does both modes, was run in UEFI mode (with no place to put the UEFI bootloaders).

---

### Post by captaincyril on 2021-10-10
Thank you for your explanations.

It is UEFI and preference for Legacy first maybe that's why it didn't work. I never had problems installing Ubuntu on Vista machines. This one is Windows 10 upgraded from Windows 7 and what's confusing is that the partitions in Windows don't look the same as the ones in Linux.

I will turn off QuickStart from Settings and will disable hibernation.

It will take me a while to find time to do this. I will definitely reply later on.

---

### Post by captaincyril on 2021-10-14
I just wanted to make sure that the steps I did were OK since it's the first time I do this. I came across this video that helps things better for starters.

[https://www.youtube.com/watch?v=rPUVIc-W13s](https://www.youtube.com/watch?v=rPUVIc-W13s)

It works for Windows 8. It should work for Windows 10. No?

---

### Post by yancek on 2021-10-14
The steps in the video you posted are correct for a Legacy install of both windows and Ubuntu if you want to boot both from windows.  They won't work at all on UEFI but since you are using Legacy, the steps will. work.  I used these exact steps to enable booting windows 7 and Linux from the windows BCD bootloader.  During the install of Ubuntu, the person installing did not accept the default of installing Grub to the MBR of that drive but rather to the partition on which Ubuntu is installed.  Doing this does not "corrupt" the MBR as indicated by the person in the video but installs Grub code there.  For windows users who want to keep windows code in the MBR, this is correct.  If a user does not have a windows installation CD or hasn't bothered to create a windows recovery CD, s/he could have problems reinstalling windows boot code although it is possible to download windows software  to do this.

Going through the process of using BCD requires an installed Linux as you see in the video (using the dd command) and as I indicated in an earlier post is convoluted.  The instructions for using BCD to boot Ubuntu took about half the video whereas installing Grub to boot both windows/Ubuntu was a simple mouse click.  If you want windows in charge, the method described will work.

---

### Post by captaincyril on 2021-10-14
Thank you for your explanation. Yes on this laptop I want Windows (Legacy) to be in charge. The other laptops of course Linux is in charge and it was quite easy.

---

### Post by captaincyril on 2021-10-16
I copied the grub info into Windows
I used bcdedit to create a partition entry, label it and sort it and it is working. It is much slower than grub.

I still have one question. Can I update the grub in Ubuntu Mate on sda6? Will it affect Windows? This grub has an additional 2 entries showing the USB partitions which I no longer need to boot on.

Thank you for all your help.

---

