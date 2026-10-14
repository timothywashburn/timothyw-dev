dump from database of largest biomes at 0,0 in mc 26.3 exported 10/14/2026

size is the 1:4 size; blocks is the blocks squared. some seeds will be verified and some won't be;
this is because I didn't think it was necessary to verify things that weren't that
notable when the verification rate has been 100%. all #1 seeds are verified

all biomes except cave ones are measured at y 256. the cave biomes are as follows:
- deep dark: -64
- dripstone: 0
- lush: -16
- sulfur: 0

the index can be converted to a seed using this bijection I didn't write:
```python
M = (1 << 64) - 1

def mix(z):
    z = ((z ^ (z >> 30)) * 0xBF58476D1CE4E5B9) & M
    z = ((z ^ (z >> 27)) * 0x94D049BB133111EB) & M
    return z ^ (z >> 31)

def seed_of(index):
    s = mix(mix(index ^ 0x5350415742494F4D) ^ 0x243F6A8885A308D3)
    return s - (1 << 64) if s >> 63 else s
```
