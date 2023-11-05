[![License Apache 2.0](https://img.shields.io/badge/license-Apache%20License%202.0-green.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![PayPal donation](https://img.shields.io/badge/donation-PayPal-cyan.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=AHWJHJFBAWGL2)
[![YooMoney donation](https://img.shields.io/badge/donation-Yoo.money-blue.svg)](https://yoomoney.ru/to/41001158080699)

# What is it?
It is a small utility to convert .BIN snapshots ([BK-0010(01)](http://en.wikipedia.org/wiki/Electronika_BK) emulator format) into sound WAV files which can be played and recognized by real BK-0010 TAP reader.   
The Project is based on [old QBasic based converter project](http://bk-mg.narod.ru/).

# Description in Russian
Утилита для конвертации BIN файлов (снапшотов для эмуляторов БК-0010 и БК-0010-01) в аудио WAV формат. Позволяет получать файлы с обычной скоростью загрузки и турбированные, пригодные к загрузке на БК-0010 через магнитофонный вход.

# What is BK-0010
[BK-0010](http://en.wikipedia.org/wiki/Electronika_BK) was the most popular soviet 16-bit home computer platform in 80-th and my first computer (still working).

# Pre-built binaries?
Pre-compiled versions of the utility can be downloaded from [the last release page](https://github.com/raydac/bkbin2wav/releases/latest).

# Known archives with snapshots
- [Online archive of BK0010 bin files](https://archive.pdp-11.org.ru/BKGAMES/BIN/)
- [Yet another archive of game snapshots (Web archive)](https://web.archive.org/web/20181019204608/http://www.bk001x.ru:80/index/na_bukvu_quot_a_quot/0-184)

# How to use it?
Initially the converter was written in [Python](https://www.python.org/downloads/) but then I made GoLang version. For Python version you have to install [Python](https://www.python.org/downloads/) but pre-compiled GoLang version can be used as simple executable files without tricks.   
The Utility is command line interface one, you can call it with listed configurations:
## Example for native version
```
bkbin2wav-windows386.exe -i Arkanoid.bin -o Arkanoid.wav
```
## Example for python version
```
python bkbin2wav.py -i Arkanoid.bin -o Arkanoid.wav
```
## Start without arguments
If start the application without parameters, then it will print list of allowed options
```
bkbin2wav -i <binfile> [-a] [-o <wavfile>] [-n <name>] [-s addr] [-t]

    Command line options:
        -h          Print help
        -f          Use file size instead of .BIN header size field value
        -a          Amplify the audio signal in the result WAV file
        -i <file>   The BIN file to be converted
        -o <file>   The Result WAV file (by default the BIN file name with WAV extension)
        -n <name>   The Name of the file in the TAP header (must be less or equals 16 chars)
        -s <addr>   The Start address for the TAP header (by default the start address from the BIN will be used)
        -t          Use the double frequency "turbo" mode
```
Sometime .BIN files may contain wrong data size value defined in their header, in the case you can use **-f** flag to enforce usage of physical file length instead of the data length defined in the BIN header.
