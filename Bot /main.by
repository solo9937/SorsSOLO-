import os
import threading
from flask import Flask
from pyrogram import Client

# قراءة المتغيرات من البيئة (Environment Variables)
BOT_TOKEN = os.environ.get("BOT_TOKEN")
API_ID = int(os.environ.get("API_ID"))
API_HASH = os.environ.get("API_HASH")
OWNER_ID = int(os.environ.get("OWNER_ID", "0"))

# --- إعداد البوت ---
app_bot = Client(
    "solo_factory",
    api_id=API_ID,
    api_hash=API_HASH,
    bot_token=BOT_TOKEN
)

# --- Flask Server (عشان السيرفر يفضل صاحي) ---
server = Flask(__name__)

@server.route("/")
def home():
    return "SOLO Factory is running!"

def run_server():
    server.run(host="0.0.0.0", port=10000)

# --- تشغيل البوت ---
def run_bot():
    print("Starting SOLO Factory Bot...")
    app_bot.run()

if __name__ == "__main__":
    # تشغيل Flask في Thread
    threading.Thread(target=run_server).start()
    # تشغيل البوت
    run_bot()
