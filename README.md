# M480BSP_Coremark

down coremark source code from GitHub as below , 

https://www.eembc.org/coremark/download.php

Porting step : 

- 1. Create folder named "CoreMark" in project , and put below file into folder : 

-- core_list_join.c , core_main.c , core_matrix.c , core_state.c  , core_util.c , coremark.h 

- 2. Put below file in project : core_portme.c , core_portme.h 

- 3. check comment between //porting Nuvoton start , //porting Nuvoton end in core_portme.c and core_portme.h

- 4. exclude main.c in project , and follow step #3 modification in core_portme.c and core_portme.h

-------------------------------------------------------------
in KEIL setting , 

- Options for Target > C/C++ , add define MAIN_HAS_NOARGC

- Options for Target > C/C++ , select Optimization > Level 3(-O3) , checked Optimization

- Options for Target > C/C++ > Include Paths  , add directories \Coremark , and \Template


in IAR setting , 

- General Options > Library Options 1 > Prinfer formattter , select Auto

- C/C++ Compiler > Preprocessor > Optimizations > Level , select High and Speed , checked No size constraints

- C/C++ Compiler > Preprocessor > add define MAIN_HAS_NOARGC

- C/C++ Compiler > Preprocessor > add directories \Coremark , and \Template

-------------------------------------------------------------
Below is my test result / score in NuMaker-PFM-M487D , 

CoreMark Size    : 666

Total ticks      : 23842

Total time (secs): 23.842000

Iterations/Sec   : 503.313480

Iterations       : 12000

Compiler version : uVision 5.26.2.0

Compiler flags   : --device DLM -O3 -Otime --apcs=interwork

Memory location  : FLASH

seedcrc          : 0xe9f5

[0]crclist       : 0xe714

[0]crcmatrix     : 0x1fd7

[0]crcstate      : 0x8e3a

[0]crcfinal      : 0xd340

Correct operation validated. See README.md for run and reporting rules.

CoreMark 1.0 : 503.313480 / uVision 5.26.2.0 --device DLM -O3 -Otime --apcs=interwork / FLASH

-------------------------------------------------------------

2K performance run parameters for coremark.

CoreMark Size    : 666

Total ticks      : 18400

Total time (secs): 18.400000

Iterations/Sec   : 652.173913

Iterations       : 12000

Compiler version : IAR 8.32.1.18631

Compiler flags   : -Ohs -no_size_constraints

Memory location  : FLASH

seedcrc          : 0xe9f5

[0]crclist       : 0xe714

[0]crcmatrix     : 0x1fd7

[0]crcstate      : 0x8e3a

[0]crcfinal      : 0xd340

Correct operation validated. See README.md for run and reporting rules.

CoreMark 1.0 : 652.173913 / IAR 8.32.1.18631 -Ohs -no_size_constraints / FLASH


