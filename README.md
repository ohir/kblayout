# Kblayout. Prints current keyboard layout on the terminal.

In its current shape this script prints configured keyboard layout
to the console. The ultimate goal is to provide mere users with a
sane way to write then compile their own layouts - by editing
the picture as produced by kblayout script piped to the file. 
```
  Usage: kblayout [options] command arg, arg file[.skd]

    commands:
      -show      print layout for gears: 1/2 3/4 5/6
                 Default if command runs as "kblayout"

    options:
      -h        this help
      -v        be verbose
      -g7       show for gears: 1/2 7/8 9/10
      -num      show edit and numeric block layout 
      -ansi     use ansi terminal codes for output (dead keys mostly)
      -wide=ch  Correct display for a wide character(s) given.
      -ovfl=ch  Correct display for a overflowing character(s) given.
```

### The GEARBOX metaphor

This configurator tool uses a "gearbox" metaphor to describe attainable
states of the keyboard: what is the result of the key being pressed depends
on what “gear” the keyboard is in.

Bare US layout uses only two gears: g1:unshifted, g2:shifted (or caps-on).
Many latin alphabet layouts use four gears: g1:unshifted, g2:shifted/caps,
g3:AltGr, g4:AltGr-shifted. The Shift and AltGr thus are “gear leversʺ in
such a layout. 

Kblayout can print all ten gears an xkb maps may have set. Below is a sample
layout obtained with `kblayout -g7` command: *(mind that github may make visible gaps between the lines)*.
```
-----¦  Short descriptions:  ¦-------------------------------------------------------------------------------------
G1:  ¦₀⃧ Ret   Return   
G2:  ¦₀⃧ Ret   Return   
G7:  ¦₀⃧ CLck  Caps_Lock
┌─────────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│ ◀⃞ ▲⃞ ▼⃞ ▶⃞ Cursor, ⌂⃜ Insert, ⌫  Backspace, ⬉⃞ Home, ▀⃞ PgUp, ▄⃞ PgDown, ⬊⃞ End, ⌧ Delete │ Gear chords ⓷▝⓹▝⓽▝, ⓷ +⓹ =⓻ │
├─────────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┬───────┤
│Eˢ᷐ ➑     │F⒈ Ɛ⃠   │F⒉ ─   │F⒊ ┌   │F⒋ ┬   │F⒌ ┐   │F⒍ ├   │F⒎ ┼   │F⒏ ┤   │F⒐ └   │F⒑ ┴   │F⒒ ┘   │F⒓ │   │⌫  ➑   │
│Eˢ᷐ ₀⃧     │ ⌂⃜ ą⃠   │F⒉ ä⃠   │F⒊ ő⃠   │F⒋ ç⃠   │F⒌ č⃠   │F⒍ â⃠   │F⒎ ă⃠   │F⒏ ċ⃠   │F⒐ ḅ⃠   │F⒑ å⃠   │F⒒ ā⃠   │F⒓ á⃠   │⌧  ➆   │
├───────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴─────┬─┴───────┤
│ ~ ʻ   │ ! 😐  │ @ 😑  │ # 😒  │ $ ➑   │ % ➑   │ ^ ➑   │ & ➑   │ * ➑   │ ( ➑   │ ) ➑   │ _ ˍ   │ + ≠   │⌧  ═     │
│ ` ʼ   │1⃞ 😛   │2⃞ 😜   │3⃞ 😝   │4⃞  ➆   │5⃞  ➆   │6⃞  ➆   │7⃞  ➆   │8⃞  ➆   │9⃞  ➆   │   ➆   │ - ±   │ = ‗   │⌫  ⌫     │
├───────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬───────┤
│ ⟽  ➑    │Q⃞  🙃  │W⃞  😷  │E⃞  ₑ   │R⃞  ➑   │T⃞  ➑   │Y⃞  ➑   │U⃞  ➑   │I⃞  ➑   │O⃞  ◌   │P⃞  ➑   │ { ⟨   │ } ⟩   │ | ǂ   │
│ ⟾  ➆    │ q🙄   │ w😬   │ e ᵉ   │ r ➆   │ t ➆   │ y ➆   │ u ➆   │ i ➆   │ o ᵒ   │ p ➆   │ [ ⁅   │ ] ⁆   │ \ ǁ   │
├─────────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴──┬────┴───────┤
│ c̶ₐ̶ₚ̶ₛ̶ ⓹ Ɛ⃠   │A⃞  ₐ   │S⃞  ʃ   │D⃞  ⟵   │F⃞  ⟰   │G⃞  ⟱   │H⃞  ⟶   │J⃞  ℑ   │K⃞ ⎇    │L⃞  л   │ : ˇ   │ " ˏ   │ ↵   ₀⃧ ➑    │
│ Gear ⓷ ⓫   │ a ᵃ   │ s ˢ   │ d ⬅   │ f ⬆   │ g ⬇   │ h ⮕   │ j ℹ   │ k⚡   │ l ˡ   │ ; ˆ   │ ' ˌ   │ENT  ₀⃧ ➆    │
├──────┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─────┴─┬─┏━━━━━━━┓┘
│ ²cₐₚₛ│ ␥⃥     │Z⃞  ζ   │X⃞  ₓ   │C⃞  ➑   │V⃞  ♪   │B⃞  ♬   │N⃞  ♫   │M⃞  ♩   │ < ♭   │ >🐧   │ ?🐳   │ ²cₐₚₛ │ ┃ ▲⃞ ↗   ┃
│Shift▝│⓽▝     │ z😀   │ x😁   │ c 😏  │ v😕   │ b😇   │ n ⁿ   │ m😖   │ , ♥   │ .🐾   │ /🐬   │ Shift▝│ ┃ ▲⃞ ↑   ┃
├─────┬┴────┬──┴──┬────┴───────┴───────┴───────┴─────┬─┴───┬───┴─┬─────┼─────┬─┴───────┴──┲━━━━┷━━┯━━━━┷━┹┬──────┺┓
│LCtl │⓷▝   │LAlt │          ⓶ _sp_  ⓼ ZWSP  ⓾ ZWNJ  │⓷▝   │⓹▝   │⓽▝   │RCtl │   ⓶ ⓼ ⓾    ┃ ◀⃞ ↖   │ ▼⃞ ↙   │ ▶⃞ ↘   ┃
│Ctrl │Win  │Alt  │Space     ⓵ _sp_  ⓻ ‸     ⓽ ˞     │Alt  │Win  │Menu │Ctrl │   ⓵ ⓻ ⓽    ┃ ◀⃞ ←   │ ▼⃞ ↓   │ ▶⃞ →   ┃
└─────┴─────┴─────┴──────────────────────────────────┴─────┴─────┴─────┴─────┘    ᵍᵉᵃʳ    ┗━━━━━━━┷━━━━━━━┷━━━━━━━┛
 Options: -g7 shows upper gears   -num shows edit keys and numpad layout   -ansi shows dead keys inverted.

```

---

## Kbconfig. Sane XKB configuration tool.

> PLANNED FUNCTIONALITY AHEAD! Not implemented yet.

If this script is run as kbconfig it produce maps that can be
directly used with `setxkbmap country -variant sane` command.

Quick configuration can be done using `kblayout` produced "picture":
```
$ kblayout > mylayout
# edit mylayout, replace or add character to the key using copy&paste
# eg. copy emoji from the browser and put it on a key.
$ kblayout -check mylayout      # lint 
$ sudo kblayout -set mylayout   # install xkb maps
# 
# From now on your sane keyboard layout persists in xkb config dir
```

Full configuration also uses a single file, but there you can also configure not only printable characters.
```
$ kblayout -skb > mylayout.skb
# edit mylayout.skb. Eg. add PgUp/PgDn actions to the '=' and 'Backspace' keys.
$ kblayout -skb -check mylayout.skb      # lint 
$ sudo kblayout -skb -set mylayout.skb   # install xkb maps
```

### kbconfig vocabulary.

> Unlike XKB's almost nonexisting documentation, kbconfig's avoids using the "shift/level/group/iso" words permutated seemingly at random. Hence:

“Symbol” is something produced by a keypress.  Usually a letter (rune,
or codepoint in unicode parlance) but also it can symbolize an action:
eg. PGUP is a symbol of a “Page Up” action.

“Layout” is a map that says what symbol should be produced if you press
a key, or more keys simultaneously. This file describes such a map.

“Shift” means the Shift key pressed and kept down before other key is pressed.

You normally do not write long sequences of “foreign” characters, but
if you do use some of them from time to time, it would be good to have
them at your index finger's reach. The kbconfig is designed for such
a use-case: a single chosen key, eg. CapsLock or Menu, acts as an
universal “gear lever” that choses an odd gear (3,5,7,9). Then the
Shift (+1) chooses next even gear (4,6,8,10).

```
  g1 - Normal run.                   G2 is with Shift or Caps Locked.
  g3 -       tap [GEAR] key once.   Then the other key. G4 with Shift.
  g5 - Shift+tap [GEAR] key once.   Then the other key. G6 with Shift.
  g7 - Shift+tap [GEAR] key twice.  Then the other key. G8 with Shift.
```
  Gears 3 and 5 can be assigned to any of control keys to be used in a
  chord. If both are pressed, the g7/g8 is on. Note that in common
  use gear3 is on the AltGr key (right Alt).

  Caps Lock state ON does a +1 gear shift for letters on g2 and g4.

  One of three predefined keys may act as a gear lever latch: CAPS, F1,
  and grave/tilde. Each is then overloaded to be still of general use:
```
  CAPS:  tap once (g3) then a key for symbols of gear3. The CAPS key
         itself becomes an additional Insert key (for vim users).
         Shift+tap ~ key thrice for Greek overlay. Then a press a letter.
         Caps_Lock state can be toggled with both shifts pressed.

  TLDE:  tap once (g3) then a key for its symbol of gear3. The grave key
         itself becomes ordinary grave/tilde key.
        ˊacute  is at g5, so Shift+tap once,  release shift, tap for ˊ.
        ˉmacron is at g7, so Shift+tap twice, release shift, tap for ˉ.
         Shift+tap ~ key thrice for Greek overlay. Then a letter key.

  F1:    tap once (g3) then it becomes an additional Insert.
         Both Ins and Shift+Ins work. Good for compact mac keyboards.
```

### Sane keyboard definition file format

Definition line is one that begins with an equal sign. Other lines are
commentary. Definition line may bear an // end-of-line comment. Definitons
may be extended using opening =+ on the following line(s).

First definition defines for good - you need not to comment out adjacent
variants while tinkering with your layouts. All you need is to move
relevant definition line to the top of other, similar ones. You will
be warned though, if such definitions are apart.

The configuration is opened by a =Keyboard line followed by a block of
description to be seen in the 'kbconfig -list keyboards' query.
The =Keyboard line further contains space separated keywords with the
language selector being first. Eg. “=Keyboard pl dvorak small mini”.

Note that Kbconfig has NO notion of languages, variants or options.
It is a single-file transpiler and always produces four xkb files
of a fixed 'sane' name.

The =CKeys directive allows one to assign physical keys to symbolic ones.

  Default pc105 codes are shown below. Swap them to set desired placement
  of all your levers. All other directives respect changes set here.

` =CKeys LCTL:37 LALT:64 LWIN:133 SP:65 RALT:108 RWIN:134 MENU:135 RCTL:105`


The =Levers directive assigns a gear lever, G3, and G5 symbols to keys.

` =Levers CAPS // is the Lever. CapsLock toggles with both Shifts pressed.`

  First is the symbol for the Lever key: NONE, CAPS, F1, F12, or TILDE

  You can assign a chord keys with key symbol after the gear: G3:RALT G3:LWIN
  You can also disable F1 with: -F1 (F1 becomes an additional Insert then,
  if pressed without shift). This is default behaviour also with CAPS as
  a Lever. Disable F1 as insert using -f1keep flag.

` =Levers CAPS G3:RALT G3:LWIN SUPER:RWIN G9:MENU // See "Extra Gears" for G9`


The US PC 105-keys physical layout looks like:
```
    ESC F1 2 3 4 5 6 7 8 9 10 11 F12        PSc ScLk PSbr
      ` 1 2 3 4 5 6 7 8 9 0 - = BKSP        INS HOME PGUP      NL P/ P* P-
    TAB  q w e r t y u i o p [ ] \          DEL END  PGDN      P7 P8 P9 P+
    CAPS  a s d f g h j k l ; ' ENTER                          P4 P5 P6 P+
    SH ■ z x c v b n m , . / SHIFT               UP            P1 P2 P3 PE
    CTL ALT WIN |space| ALT WIN MNU CTL     LEFT DN RIGHT        P0  PD PE
```

Layouts are defined by seven blocks, each headed by the (fixed) key row header:
```
 =Funcs  ESC    F1   F2   F3   F4   F5   F6   F7   F8   F9   F10  F11  F12  DEL
 =Digit  `   1    2    3    4    5    6    7    8    9    0    -    =    BKSP
 =Tab    TAB  q    w    e    r    t    y    u    i    o    p    [    ]    \
 =Caps   CAPS  a    s    d    f    g    h    j    k    l    ;    '    ENTER
 =Shift  LSGT   z    x    c    v    b    n    m    ,    .    /    SPACE
 =NumPad P0   P1   P2   P3   P4   P5   P6   P7   P8   P9   P/   P*   P-   P+
 =EdMov  P.   PENT INS  HOME END  PGUP PGDN UP   DOWN LEFT RIGHT
```
Unlike with xkb files, you need not to know hex notations of a codepoint to
make your layout source.  Kbconfig expects you to just enter the symbol of
interest. Copy-paste it from the web or from the "Characters Map" utility.
Resulting keyboard configuration file keeps to the WYSIWYG principle so
it IS-A layout documentation.

Whole layout definition is made of the symbol lines that begins with gear
number followed by a symbolic Shift position: 1_ 2- 3_ 4- 5_ 6- 7_ or 8-.
There you can move symbols and actions at will (almost). Eg. Belgian AZERTY
layout =Tab block will have letters moved to the respective azerty positions:

```
 =Tab    TAB    q    w    e    r    t    y    u    i    o    p    [    ]     \
 =1_:    TAB    a    z    e    r    t    y    u    i    o    p   .â    $    ..
 =2-:    TAB    A    Z    E    R    T    Y    U    I    O    P   .ä    *    ..
 =3_:   HOME    ..   ..   €    §    þ    ..   ..   ..   œ    §    [    ]    ..
 =4-:   HOME    ..   ..   ..   ®    Þ    ..   ..   ..   Œ    ¶    ⁅    ⁆    ..
 =5_:    END    ..   ..   ..   ..   ᵗ    ..   ..   ..   ..   ℘    PGDN PGUP ..
 =6-:    END    ..   ..   ..   ..   ₜ    ..   ..   ..   ..   ℙ    PGDN PGUP ..
```

The `..` stands for “default gear marker symbol”, then `.â` and `.ä` symbols
picturize dead-accent on the key.


### Dead accents

“Dead key” is an input method, not a part of unicode.  With dead-key you do
not see the accent until after the second keypress and resulting accented
letter usually comes as a single (precombined) character. Dead accents are
set on a key by the dot followed by a first small latin letter that uses
given accent (first as per codepoint number) or a hex number. Note that
most 'hex' dead accents is really dead on latin terminals, though.

Copy/paste from here:

```
                     ### DEAD KEYS TABLE ###
   .ƈ dead_hook       .Ɛ  dead_greek                .ɩ  dead_iota               
   .ơ dead_horn       .ċ  dead_abovedot             .â  dead_circumflex         
   .à dead_grave      .¤  dead_currency             .ő  dead_doubleacute        
   .á dead_acute      .ḅ  dead_belowdot             .ȁ  dead_doublegrave        
   .ã dead_tilde      .ḁ  dead_belowring            .ḇ  dead_belowmacron        
   .ă dead_breve      .ä  dead_diaeresis            .v  dead_voiced_sound       
   .č dead_caron      .å  dead_abovering            .ȃ  dead_invertedbreve      
   .ą dead_ogonek     .’  dead_abovecomma           .ṳ  dead_belowdiaeresis     
   .ø dead_stroke     .ș  dead_belowcomma           .ḓ  dead_belowcircumflex    
   .ā dead_macron     .ḛ  dead_belowtilde           .˅  dead_semivoiced_sound   
   .ç dead_cedilla    .ḫ  dead_belowbreve           .‘  dead_abovereversedcomma 
   ._ dead_lowline    .˥  dead_aboveverticalline    .˩  dead_belowverticalline
   .80 dead_a         .81 dead_A                    ./  dead_longsolidusoverlay 
   .82 dead_e         .83 dead_E                    
   .84 dead_i         .85 dead_I                    .65 dead_abovereversedcomma       
   .86 dead_o         .87 dead_O                    .8a dead_small_schwa   
   .88 dead_u         .89 dead_U                    .8b dead_capital_schwa
```

A few more 'dot' symbols can be used:
`..` use defaults. If key was not assigned, it produces ➂ ➍ ➄ ➏ ➆ ➑ gear mark.
`.=` void symbol. Prints nothing but in some apps counts as a "key pressed".
`.-` no symbol.   Means "do not assign a symbol now/here".


### Combining characters

Unlike being “dead”, the “combining” trait of a character is a part of the
unicode standard.  Combining character “steps back” and overlays whatever
was printed there before. What you see as one glyph can be made of two or
more pieces having separate codepoint numbers. Real combining accents
are configured on the key as themselves overlayed on the dotted ring ◌:
Unicode knows over a 2000 of combining characters and accents. The basic
U+0300 combining characters/accents block is given below (to copy&paste).

#### U+0300 combining accents
```
◌̀  ◌́  ◌̂  ◌̃  ◌̄  ◌̅  ◌̆  ◌̇  ◌̈  ◌̉  ◌̊  ◌̋  ◌̌  ◌̍  ◌̎  ◌̏  ◌̐  ◌̑  ◌̒  ◌̓  ◌̔  ◌̕  ◌̖  ◌̗
◌̘  ◌̙  ◌̚  ◌̛  ◌̜  ◌̝  ◌̞  ◌̟  ◌̠  ◌̡  ◌̢  ◌̣  ◌̤  ◌̥  ◌̦  ◌̧  ◌̨  ◌̩  ◌̪  ◌̫  ◌̬  ◌̭  ◌̮  ◌̯
◌̰  ◌̱  ◌̲  ◌̳  ◌̴  ◌̵  ◌̶  ◌̷  ◌̸  ◌̹  ◌̺  ◌̻  ◌̼  ◌̽  ◌̾  ◌̿  ◌̀  ◌́  ◌͂  ◌̓  ◌̈́  ◌ͅ  ◌͆  ◌͇
◌͈  ◌͉  ◌͊  ◌͋  ◌͌  ◌͍  ◌͎  ◌͏  ◌͐  ◌͑  ◌͒  ◌͓  ◌͔  ◌͕  ◌͖  ◌͗  ◌͘  ◌͙  ◌͚  ◌͛  ◌͜  ◌͝  ◌͞  ◌͟
◌͠  ◌͡  ◌͢  ◌ͣ  ◌ͤ  ◌ͥ  ◌ͦ  ◌ͧ  ◌ͨ  ◌ͩ  ◌ͪ  ◌ͫ  ◌ͬ  ◌ͭ  ◌ͮ  ◌ͯ  U+036F [◌ is at g8-O ]
```

#### Function keys:
Fx function key, with x being in 1..20 range (F1 .. F20).

#### Actions:
UP DOWN LEFT RIGHT PGUP PGDN HOME END INS DEL BKSP

Lock key symbols: NMLK PSCR SCRL PAUSE should NOT be used.
Kbconfig does not allow to change or override preconfigured locks, nor it
allows to configure lock behaviour. This intails too much complexity and
would often produce layouts that can lock user out of her keyboard (and
machine). If you need your own locking behaviour, read Xserver and XKB
sources (these are the only documentation up-to date) then tinker
yourself with xkb layouts source and xkbcomp.
Ie. if you want to customize locks, kbconfig is not for you.

#### Keypad:
Keypad symbols have a `#` prepended. It allows to make distinction even
if "kepad's" symbol is put on any other key. For some apps it matters.


### Extra Gears.

Nobody (almost nobody) knows that your Linux keyboard input socket is 
(and for decades it was) equipped with sophisticated and powerful eight-gear
transmission box. Frankly: it is equipped with four such gearboxes that can
be swapped one for another on-the-fly.

Kbconfig configurator knows about documented eight gears, and about next
four hidden within input system code. It means that kbconfig may enable
you to use all twelve gears you have, if you desire so.

The g11,g12 are predefined Greek letters (turned on using the GEAR key),
but g9,g10 are configurable. You can enable them in =Levers directive,
eg. as g9:MENU, g9:LSGT, or g9:LWIN. 

Symbols for extra two gears are not preserved in the system configuration
and must be loaded on demand (or from scripts) with 'kbconfig -g9 file'.
Format of such is same, just with only =9_: and =10-: leads.
The g9 overlay is good for extending IDEs with one-key macros.
Note that g9/10 can be locked-in using NumLock (using mod2 lock).

